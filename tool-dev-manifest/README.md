# Tool Developer's Manifesto
A living guide for tool developers

## Abstract
Tool development is a lesser talked about discipline of software development but can play a critical role in the productivity and performance
of a team. This document is meant to give tool developers or those interested in the roles of tool developers a reference guide to things to
consider when developing tools. The hope for this guide is to help those interested in making good tools to avoid common pitfalls and develop
solid tooling right out of the gate while also being ready to iterate and evolve the tool as needs arise.

My particular experience is with the development of tools for customer service representatives, game designers, artist and other engineers, as well
as product managers and producers. All of these difference consumers have their own workflows and needs for the tools that they use, but it is necessary
to establish a core set of values and procedure for ensuring that they are being provided with the highest quality tooling to fit their needs.

## What is a tool developer
A tool developer is a discipline of software developers that focus on the creation, maintainence and development for tools used by usually non-technical
and other technical peers in a workplace. A tool developer should focus on the needs of these consumers and monitor how the consumers are using the tools
and listen to consumers for their needs and struggles with using the tools. 

A tool developer should not be bound to any particular stack of technology or language. Tool needs to be where a tool needs to be. 

### Case Study: I want to upload a CSV into the tool
The consumer is a game designer. They have been working in Google Sheets to develop a spreadsheet that contains balance data. They like using Google Sheets because 
they are comfortable with the mathetical functions and graphing capility that the software provides and they feels like they can easily iterate on the data. But they also
now want this data to appear in the game. They know that usually data that appears in the game can be entered into a tool so they make a request that they would like the tool
to support uploading a CSV, exported from Google Sheets.

Let's model this workflow
1. Data entry into Google Sheets
2. Graphing data in Google Sheets
3. Iterating on data
4. Exporting CSV from Google Sheets to the local file system
5. Opening the tool for game data
6. Navigating into the tool to the CSV uploader
7. Uploading the CSV from the local file system into the tool
8. Checking the data in the product

So how do we evaluate this request and what this will mean for the tool?

## What is a tool
A tool is a step in a workflow. While the role of tool developer may indicate that the developer would only focus on developing a tool, in reality, a tool lives
as part of a broader workflow that consumers step through to accomplish their day to day tasks. A tool developer must never forget that a tool is merely
a step in a workflow and not all consumers issues with a tool can or should be solve merely by modifying the tool

### Case Study: Starting off your day
In the morning, the consumer gets into the office and wants to see how many people logged into the product over the last 24 hours

Their workflow may look like this:
1. Go to their desk
2. Open their computer
3. Log into their computer
4. Open up a web browser
5. Open up a web tool that contains monitoring for the people in the product
6. Navigate the web tool to a dashboard that contains the number of people that that have logged into the product
7. Filter the dashboard for that last 24 hours

Does this workflow need optimization? Where can we optimize the workflow?
Maybe. It should be an active discussion with your team about whether this workflow should be improved.
Step 5 - 7 could be optimized by making the main page for the web tool be the last 24 hours dashbaord view, saving 3 steps. But if other consumer workflows involve
navigating to other portions of the site, this may increase their workflow duration and overall be a net-negative for the team.
Step 4 - 5 could be optimizeed by either making the default page of the browser be the web tool or by having a shortcut to the web tool on the consumers desktop. But this must be maintained on each consumers
working environment and therefore now becomes a step of the onboarding process.
Step 1 - 3 could be optimized by having a dedicated television setup in the office streaming the given dashboard, saving all the steps. But this television now becomes part of the
maintenance load of the tools team.

There's probably more ways of addressing this workflow, and the right ways can only be determined by the team choosing what constraints it cares about.

## Workflow
A tool developer should treat the workflow for the tools as important as the tool itself. A good tool that is hard to incorporate into a workflow is not a good tool at all. It is important to define the consumer
workflows that intersect with the tool, the steps of the workflow that the tools inhabit, and keeping a live understanding of how consumers are interacting with the tools in their workflows to 
fully understand when consumers have new needs or request for the tool. Many times, consumers will assume that a workflow issue can only be addressed by a change to the tool, but sometimes it is the workflow itself
that needs to be more fundamentally reaccessed. 

A good practise is to keep an up-to-date model of various workflows that your consumers have, highlighting which steps of the workflow are contained with the tools you develop, and estimate the duration of each step.
How fine-grain this workflow modeling is up to you, but keep it to the level of detail that is actually addressable. For example, having steps be "Finding a button" and "Clicking a button" are good for their detail, but 
may lack addressability for looking for workflow optimizations. That said, if "Finding a button" takes a non-trivial amount of time, then it should be addressed.

Modeling a workflow can be done as a list of steps as seen in the above case studies, or as a diagram. Choose a format that suites your needs. However you model workflow should be easily accessible, iteratable,
and sharable across your team. The best scenario is when the team is contributing to this list and giving feedback and highlighting sore spots in the workflow. This should drive the focus of tool
maintenance.

## Documentation
Do this.

The best kind of documentation for a tool is a tool that documents itself. Use tooltips, use description paragraphs. If your documentation is external, insert links into the tool to those documentations. If the external documentation cannot be linked to, add descriptions within the tool for how a consumer can find that documentation. Consider consumer onboarding as part of the workflow for using the tool and every step of a consumer's workflow where they are interacting with the tool is a step where they may not know the next step and need to find it.
