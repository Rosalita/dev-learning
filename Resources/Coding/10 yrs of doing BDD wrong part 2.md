# 10 yrs of doing BDD wrong pt 2
## by Liz Keogh 
#video #watched on 03-01-2021

tags 
#development #bdd

[10 yrs of doing BDD wrong part 2](https://www.youtube.com/watch?v=AFCdE5KSREI)

Synopsis: Waterfall fails because it doesn't take into account the fact that you discover things. The value happens in the project where the new thing happens. The new thing is differentiator. A kata are very simple, very predictable exercises like turning numbers into roman numerals. We frequently use katas to learn new things, like TDD or a new language. Estimates work best when things are simple and predictable. If things are new and we have never done them before, we have no idea what will happen, yet we estimate them in story points. Instead, estimate complexity. High complexity is something noone has done before. Low complexity is something we all know how to do. Most startups don't spend their time writing BDD scenarios, they get something out and get feedback from it.

Patterns for BDD

#### Context Questioning. 

Is there a context in which this event will create a different outcome? In the example of the cash machine, if I request £20 is there a context where the cash machine pixie does not give me £20? Yes, when no money in your bank account. Is there a context when I can have no money in my bank account and still get £20, yes when I have an overdraft. This is how to discover scope creep with these questioning patterns.

Is there a stakeholder for whom this application will not meet their goal?

Are all of the stakeholders goals met by this?

If we could deliver it with pixies, would it be enough?

#### Feature Injection. 

Don't do anything unless you absolutely need to. The primary stakeholder has a vision which makes money, saves money or protects money. There are also stakeholders whose goals are needed to go live. These are gatekeeping stakeholders which will stop us going live unless we meet their needs. Have conversations with them. In order to deliver people's goals, we deliver capabilities. A feature is something you can use. A story is a slice through a feature to get feedback on it quickly. Scenarios are used to split up stories they are examples of how the system might behave from the perspective of the user. Then code turning ideas into reality. The person that tends to know what's going on is the person that has to turn the idea into code. 

Feature injection looks like

- Vision
- Goal
- Capability
- Feature
- Story
- Scenario
- Code

Testers have deliberate discovery skills. They know how they are going to find bugs in code. By putting testers with their deliberate discovery skills into the conversation first because they think of the scenarios we miss. This results in less rework. You will always have to rework some of your app, otherwise it wasn't an app worth building. The business analyst, developer and tester are the three amigos.

BDD is a sense making tool, like cynefin. It works well between complicated and complex. A real project is made from discoveries. We are learning how to discover stuff by doing it and helping other people do it. The different levels of abstraction in feature injection are there to help you get feedback. Make as small a commitment as possible, then get feedback. Do the riskiest stuff first and get feedback.

#### Deliberate Discovery
- Assume ignorance
- Assume second order ignorace
- Optimise for discovery, do the new stuff first

Standup template
- This is what I learned yesterday
- This is what I hope to find out today

if you focus on this its usually valuable for the rest of the team too.

#### BDD

We know how log in works, we never needed to have a conversation about how login works. For the simple things, like adding two numbers together, we don't need these BDD scenarios.

If we get into the CRUD space, name the scenarios and move on. Create the user, read the user, update the user, delete the user.

Ask the question, is there anything different about this scenario compared to how it normally works?

If you say "We can't accept this into our backlog without clear acceptance criteria" Every time you do this you are pushing back on the uncertainty. Don't let your process hide your ignorance.