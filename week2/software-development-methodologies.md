Software Development Methodologies
===============================

__Q__: What is the traditional development life-cycle?
---------------------------------------------------------------------
__A__: The life-cycle of traditional software development consists of the following stages:

![Traditional software dev life cycle](https://online.husson.edu/wp-content/uploads/2016/03/627x627-SftwareDev-Feature-HUSS.jpg)

__Planning & Analysis__: In this stage, developers meet with the clients to discuss their concept of the project, as well as the main features they would like to implement.

__Design__: In this stage, UX and web designers take their brief and begin to design mockups of the product known as _wireframes_ which focus on the aesthetic and feel of the product.

__Implementation__: In this stage, developers take the designs and begin to translate them into workable code.

__Testing & Integration__: The code is checked for bugs and optimised for brevity/efficiency until it is considered to be ready for release.

__Maintenance__ *(AKA Evolution)*:  The code is maintained over time by developers who make sure that it continues to function as it should. If any bugs are picked up IRL that weren't clear in the testing stage, they will be addressed here.

This chronological way of developing software is known as the __waterfall__ method. We will discuss this further in the next question...

__Q__: How does agile differ from traditional waterfall methodologies?
----------------------------------------------------------------------------------------
__A__: In the __waterfall__ method, developers work incrementally towards a final product. The stages of development are sequential; they happen *one after the other*. Once the design stage is completed, development can occur. Once the development stage is over and the final product is made, testing can begin, and so on.

![Waterfall software development life cycle](https://xbsoftware.com/wp-content/uploads/2014/10/software-development-life-cycle.png)

The __waterfall__ method certainly has its uses, but there are some flaws in its applications:

 - Waterfall is not an efficient use of time or financial resources.  Because it works sequentially, each team has to wait until the completion of the team before them before they can begin work. 
 - In waterfall, no feedback is gained from the client until the end of the cycle. Sometimes, developers will work on a project until completion, only to show it to a client who is dissatisfied with the work. Simple problems that could have been avoided at earlier stages are now set in stone.
 - As testing is the last stage in the cycle, it is often the stage that is given the least attention, especially if a project runs out of time or money. This translates to poorer quality code.
 - In waterfall projects, there is often a hierarchical network of _teams-within-teams_. This means that, especially on larger projects, there is poor cross-department communication, which can impact the quality of the code.
 - In waterfall, a product won't emerge until the later stages of the project. This means that it is difficult to accurately estimate the time it will take to complete. Until someone has started work on coding or testing, it will be unclear how much time and effort these stages will take.
 
----------
In order to address these issues, the __Agile__ process has emerged. It follows a similar methodology with some key differences.

![Agile vs waterfall web development](http://www.agilenutshell.com/assets/how-is-agile-different/continuous-activities.png)

In __agile__ software development, the stages of work are the same, but they occur multiple times, on a feature-by-feature basis. The aim is to create a __MVP__ (or *Minimum Viable Product*) consisting of only the most necessary features of the product within a shorter time span than with waterfall (usually **2-4 weeks**). After this has occurred, the developers can pivot their project based on initial feedback from clients and real-world testing on a much faster basis than through the waterfall method. Each feature will usually have dedicated smaller teams (think the **git branches** we used on our projects last week). When a feature is considered completed, the smaller team will advance 

Despite all of the great things about using **agile**, it has some limitations:

 - By its very definition, agile is a lot less predictable than waterfall. As there is no final plan the team is working towards, the end product might end up looking a lot different from what people had originally anticipated.
 - Agile is difficult to operate in more traditional large companies with strict hierarchies. Because the development team are unable to present management with strict deadlines or budgets, it could quite possibly cause friction within the company.
 - Agile is an incredibly labour-intensive process. Turning out an MVP in two weeks is time consuming and potentially more stressful for the developers involved. In addition to this, agile allows you to fail fast, earlier on. Often, sprints (short, intense time periods to deliver an iteration of software) are unable to finish on time because of issues that may arise.
 

This is not to say that the **waterfall** method doesn't have its uses, however:

 - The extra time put into the preliminary stages of software development gives the client a clear-cut idea of time and budget.
 
 - In larger companies specifically, waterfall works well in internal software development (built for the company instead of a customer). This is because there is no need for customer input, and the client already knows what they have to expect.
 
 - In certain situations, it is crucial that there is a lengthy planning process followed before actual development work can begin. When companies are dealing with sensitive data, for example (think **money transfer services** or **legal firms**), it is really important that the documentation and planning is really solid. There can be no testing through iteration when you are PayPal, for example, because the consequences could be catastrophic.

__Q__: How does the general software development life-cycle differ from the TDD cycle?
----------------------------------------------------------------------------------------

__A__: In TDD, there is an emphasis on testing first before you continue to coding your project which informs the rest of your work. This has a clear difference to the usual cycles of software development in which testing is the final stage before release. By giving testing this prominence in the development cycle, we are writing code from the off that is more results-orientated. The developers need to conceptualise what they need their code to do from the beginning, which will inform the style of code that they write. Code written through TDD tends to be more maintainable, with greater coverage, than code written without it.

![Test Driven Development](http://www.agilenutshell.com/assets/test-driven-development/tdd-circle-of-life.png)
