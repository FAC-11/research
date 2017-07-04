# Technical Spikes

## What is a technical spike?
You would use a spike to figure out answers to tough technical or design problems. A spike solution is a very simple program to explore potential solutions. Spike are only built to address the problem under examination and ignore all other concerns. Most spikes are not good enough to keep, so expect to throw it away. Spikes are used for stories or outcomes which the time or cost cannot be estimated until they are  investigated and the goal is reducing the risk of a technical problem or increasing the reliability of a user story's estimate.


Broadly:

analysis of the overview and breaking into tasks is a _functional spike_. 

gaining new information on proposed or prototyped implementation and strategy is a _technical spike_



## When and why would you use a spike?
* When a technical difficulty threatens to hold up the system's development put a pair of developers on the problem for a week or two and reduce the potential risk
* If your team is having trouble on estimating the size of the user stories 
  
*    If accurate estimates are crucial because there is no contigency for project overrun.
    
 *   In building a complex architecture to allow the architecture to develop rather than being fully designed upfront as BUFD.
 *   Mitigating risk: Customers frequently come to us with an idea and, under tight time constraints, we need to validate that we can develop a component using a technology that we’re not entirely familiar with as it is impossible to keep up with all of the technologies out there. We don’t want to make any promises we can’t keep. Undertaking projects with bad assumptions can turn out badly. It can be very unsatisfying for a client, very damaging to reputation, and very expensive. This is an inherent risk in development. Focused technical spikes are a great way to mitigate this risk.
  


## How would you successfully spike on a topic
 1. ** Define a goal **
The most important thing to do when spiking a solution is to define your goal. Defining a goal provides focus. Without focus, you’ll waste valuable time doing too much. Remember, you’re singular purpose is to vet a solution. You want to gain confidence that you can accomplish something, not actually accomplish it. Remember, code developed during most spikes is meant to be thrown away. If you find, given the constraints of the project, that you can’t accomplish a task, you’ve done your client a huge service.

2. ** Limit your scope **
Just because your spike isn’t meant to deliver production ready code, doesn’t mean you shouldn’t start with a plan. The more you intentionally limit the scope of your spike from the beginning, the faster you can move towards your goal. What is really important? What knowns can be faked out, simulated, or stubbed to more quickly vet the unknowns?

3. ** If the goal is too broad repeat, if not evaluate the solution **
Ensure that you have small, focused, and independent goals to meet your needs. Doing so will allow you to move forward with greater confidence that you could meet our customer’s deadline.
 
 ----
 
#### Best Practise 
You would pair with someone but spike with different approaches to solve the same problem. Each will research and code independently and compare their notes during the day.

 Unlike production code, spikes are isolated, small, throwaway code; therefore, don't have to adhere to extreme programming  mandate by being pair-programmed code. This leads to multiple solutions which is better practice to avoid confirmation bias.

## Examples of when a spike would have helped in week 1

## Resources 
[Extreme Programming](http://www.extremeprogramming.org/rules/spike.html)


Spike is a part of a sprint.
Sprints are directed by a coach, normally pair-programmed.

In spikes, a team works on an action which is better done in a group.
For example:
* Familiarizing the team with new hardware or software they will all use or link in with.
* Dividing up tasks by first analysing the problem to be solved
* Uncovering new issues.




Some info:
**Spikes**

spikes can be used for activities such as research, design, investigation, exploration, and prototyping. The purpose of a spike is to gain the knowledge necessary to reduce the risk of a technical approach, better understand a requirement, or increase the reliability of a Story estimate.


What is a spike in Scrum?
In agile software development, a spike is a story that cannot be estimated until a development team runs a timeboxed investigation. The output of a spike is an estimate for the original story




http://www.scaledagileframework.com/spikes/

Spikes 
Spikes are a type of exploration Enabler story in SAFe. Originally defined within XP, spikes are used for activities such as research, design, investigation, exploration, and prototyping. The purpose of a spike is to gain the knowledge necessary to reduce the risk of a technical approach, better understand a requirement, or increase the reliability of a Story estimate. Spikes primarily come in two forms: technical and functional. 
Functional spikes are used to analyze aggregate functional behavior and determine how to break it down, how it might be organized, and where risk and complexity exist, in turn influencing implementation decisions. 
Technical spikes are used to determine feasibility and impact of design strategies. Like other stories, spikes are estimated and are demonstrated at the end of the Iteration. Spikes also provide an agreed protocol and work flow that Agile Release Trains use to help establish viability of upcoming Portfolio, Value Stream, and Program Epics.

details
Agile and Lean value facts over speculation. When faced with a question, risk, or uncertainty, rather than speculating about the outcome or jumping to a Solution, Agile Teams conduct small experiments before moving to implementation. Originally defined in XP, Spikes are a specific type of Enabler story in SAFe. Teams may use spikes in a variety of situations: Estimate upcoming Features and Capabilities to analyze the implied behavior, so they can be split into smaller, estimable pieces Perform feasibility analysis and other activities that help determine the viability of Epics Conduct basic research to familiarize themselves with a new technology or domain Gain confidence in a technical or functional approach to reduce risk and uncertainty Spikes generally involve creating a small program, research activity, or test that demonstrates some aspect of an upcoming feature. 

Technical and functional spikes 
Generally, there are two types of spikes: functional spikes and technical spikes. Functional spikes are used whenever there is significant uncertainty as to how a user might interact with the system. Functional spikes are often best evaluated through some level of prototyping, whether it be user interface mock-ups, hardware prototypes, wire frames, page flows, or other techniques suited to elicit feedback from the Customer or stakeholders. 
Technical spikes are used to research various technical approaches in the solution domain. For example, a technical spike may be used to determine a build-versus-buy decision, to evaluate the potential performance or load impact of a new user Story, to evaluate specific implementation technologies that can be applied to a solution, or for any reason when the team needs to develop a more confident understanding of a desired approach. Some features and user stories may require both types of spikes. Here’s an example: As a consumer, I want to see my daily energy use in a histogram so that I can quickly understand my past, current, and projected energy consumption. In this case, a team might create two spikes: Technical spike: Research how long it takes to update a Customer display to current usage, determining communication requirements, bandwidth, and whether to push or pull the data Functional spike: Prototype a histogram in the web portal and get some user feedback on presentation size, style, and charting


http://agiledictionary.com/209/spike/
Spike
A task aimed at answering a question or gathering information, rather than at producing shippable product. Sometimes a user story is generated that cannot be well estimated until the development team does some actual work to resolve a technical question or a design problem. The solution is to create a “spike,” which is some work whose purpose is to provide the answer or solution.


https://en.wikipedia.org/wiki/Spike_(software_development)
‘A spike is a product-testing method that is used to determine how much work will be required to solve or work around a software issue. Typically, a 'spike test' involves gathering additional information or testing for easily reproduced edge-cases. The term is used in agile software development methodologies like Scrum or Extreme Programming.’

A spike in a sprint can be used in a number of ways:[1]

As a way to familiarize the team with new hardware or software
To analyze a problem thoroughly and assist in properly dividing work among separate team members.
Spikes tests can also be used to mitigate future risk, and may uncover additional issues that have escaped notice.
A distinction can be made between technical spikes and functional spikes. The technical spike is used more often for evaluating the impact new technology has on the current implementation. A functional spike is used to determine the interaction with a new feature or implementation.

Following a spike, the results (a new design, a refined workflow, etc.) are shared and discussed with the team.




