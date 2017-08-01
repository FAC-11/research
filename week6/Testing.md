# Testing Databases

## What JavaScript / Node.js tools are available for testing a database?
Other than tape, you can use "mocha" and "chai" modules for testing.
Useful links:
Unit test with mocha and chai
[https://www.sitepoint.com/unit-test-javascript-mocha-chai/]
Developing a RESTful API with Node, Express, Knex - a SQL query builder - and PostgreSQL using test driven development (TDD).[http://mherman.org/blog/2016/04/28/test-driven-development-with-node/#.WYCNjnUrIfw]

## Why would you mock a database and how does this help with testing?
Create a new database that is identical to first one, and build a new url to access the mock database which will be used in the tests.

## Research testing a mock database with tape and prepare a short demonstration of how you would do this.

1. Duplicate your database folder in the test folder
2. Dreate a new database on your local machine in terminal.
3. Create an new test url in your config.env
4. At the top of your tests require in ```fs``` and ``` db_connection```
5. Copy the contents of db_build.js ```const sql = fs.readFileSync(`${__dirname}/db_build.sql`).toString();```, ```dbConnection.query(sql, (err,res) => {
  if (err) throw err;
  console.log('superheroes table created with results: ', res);
});``` This will rebuild your mock database at the beginning each time you run your tests.
6. Create a new tape test and call dbConnection.query. Inside of this function you can insert the SQL query you would like to test - **NOTE that your t.equals/deepEquals and t.end need to be called inside of the anonymous callback**
7. eg
```
const tape = require('tape');
const dbConnection = require('../database/db_connection.js');
const dbBuild = require('./test-database/db_build.js');
const fs = require('fs');

const sql = fs.readFileSync(`${__dirname}/test-database/db_build.sql`).toString();

 dbConnection.query(sql, (err, res) => { //query takes a connection from the Pool and runs a query with that connection
    if (err) throw err;
});

tape('initialising tape', (t) => {
  t.equals(1, 1, '1 should equal 1');
  t.end();
});

tape('dbConnection SELECT', (t) => {
  const expected = [{
      id: 1,
      name: "Wolverine",
      superpower: "Regeneration",
      weight: 300
    },
    {
      id: 2,
      name: "Captain Marvel",
      superpower: "Shoots concussive energy bursts from her hands",
      weight: 165
    },
    {
      id: 3,
      name: "Iron Man",
      superpower: "None",
      weight: 425
    }
  ];
  dbConnection.query('SELECT * FROM superheroes;', (err, res) => {
    if (err);
    const actual = res.rows;
    t.deepEquals(actual, expected, 'dbConnection connects to the sql database using SELECT');
    t.end();
  });
});

tape('dbConnection INSERT', (t) => {
  const expected = {
    id: 4,
    name: 'Storm',
    superpower: 'Controls the Weather',
    weight: 140
  };
  dbConnection.query("INSERT INTO superheroes (name, superPower, weight) VALUES ('Storm', 'Controls the Weather', 140);", (err, res) => {
    if (err) console.log(err);
    dbConnection.query('SELECT * FROM superheroes;', (err, res) => {
      if (err);
      const actual = res.rows[3];
      t.deepEquals(actual, expected, 'dbConnection connects to the sql database using INSERT');
      t.end();
    });
  });
});
```
