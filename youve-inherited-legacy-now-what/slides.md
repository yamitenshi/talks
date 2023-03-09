---
title: You've inherited a legacy codebase... now what?
theme: moon
verticalSeparator: \n\n--\n\n
---

# You've inherited a legacy codebase

--

...now what?

---

## About me

- Hi! I'm Nash
- I make software
- I often talk about things
  - Sometimes people listen!

---

## The 3-step program

--

![Step 1: lie down, step 2: try not to cry, step 3: cry a lot](img/cry-a-lot.jpeg)

---

## Step 0.5: Rethink legacy

- Legacy has stood the test of time

Note: 
Legacy is probably what's paying your salary. There's a reason this software exists and a reason your company wants it. The codebase might suck, but as a functional unit there's often a good reason for its existence. Embrace that!

Spaghetti code in production is almost always more valuable than beautiful code in development.

---

## Scenario 1

### The codebase is well-tested and documented

--

Congratulations! You're done. You win at life.

---

## Scenario 2

### The codebase is less than ideal

---

## Step 1: Talk to people outside your team

- What does the software do?
- Why does the software do it?
- Who is it for?
- How do they use it?

Note: 
Ask people to show you how they use the software!

--

## Step 1.5: Talk to people in your team

- What can you and your team do?
  - What can you and your team _not_ do?
- What risks are okay to accept?
- What do you _need_?
- Document all of this!

Note: 
When assessing risks, make risk models! They don't have to be perfect, just have some idea of what can go wrong and how bad it is. 

Documentation will be outdated as soon as you write it. This is okay! Having some idea is better than having no idea.

---

## Step 2: Get the thing to run

- Chart dependencies
  - Not just packages, also PHP versions, plugins, commandline tools, databases, etc.
  - Look for files that indicate dependencies
- Start simple! Just run it on your laptop or a VM.
- See if you can get it deployed
- Get someone to use it and see what's broken

Note: 
If the software doesn't run at all, there's nothing you can do. Get it running, then worry about the rest. 

Now is not the time for code quality improvements, best practices, etc. - if heaps of spaghetty and dirty hacks are what it takes, do it. You can make it pretty later.

Dependencies can be listed in things like composer.json/package.json, but also docker-compose files, Dockerfiles, deployment scripts, etc.

Try not to stray too far from your own infrastructure, but accept that your infrastructure may need to change to get this thing running.

When deploying the software, see what else is needed - API keys, external infrastructure and accounts, different environments, access controls, etc.

---

## Step 3: It Works!™ Let's keep it that way.

--

## Step 3.1: Prioritise

- Companies do things for three basic reasons:
  - To make more money
  - To reduce costs/risks
  - Because it "feels" right
- One piece of software can do multiple things
- Find out which functionalities are most important and why
  - You should have a basic idea already (see step 1) but don't stop talking to people
  
Note: 
It's important that all of this is made explicit and documented. Don't make these decisions purely with your team - the people who stand to gain or lose something should have a deciding voice in what's important.

--

## Step 3.2: Add tests

- Start on the most functional level
  - E2E tests are separate from the codebase, but ensure the software "works"
- Make the tests part of a CI pipeline or similar
- Cover the important bits
- Unit testing is not a priority
  
Note:
The goal here is not to ensure nothing breaks. The goal here is to ensure nothing breaks in a catastrophic way that ends up costing someone a lot of money.

Blocking deployments if these fail is crucial - breaking tests at this point means something is horribly wrong.

When deciding what to cover, refer to earlier talks about what's important and why, and about acceptable risks. Cover what cannot break.

Unit tests are nice and good, but not the important part here. The individual parts are not what you're looking to test for now.

---

## Step 4: What's next?

- It depends
- You've tested the important bits - now improve the code
- Stuff will break, add tests when it does
- Not all bugs need fixing (right away)
- Test as you go
- Refactor as you test
- Make concrete plans for improvement

Note:
Having the functionality covered means you can now cover the code and refactor as needed.
When adding tests, the codebase will get in the way. Make changes as needed to make things testable.
The E2E tests should ensure nothing important breaks in a bad way.

If all of this is hard and risky, you skipped ahead - go back to step 3, you're not done.

Bugs are no different from feature requests: some are not important, and some are less important than others. Prioritise them just like anything else.
Earlier conversations about what's important can help with this.

Static analysis is wonderful for this - it catches entire classes of bugs, and with a baseline can only block problems with what you've touched.

---

## Step 5: Profit(?)

Note:
There should now be a working piece of software and a solid foundation to work off.

It's gonna suck for a bit, but you can work to make it not suck, and should now have defined plans to do just that.

---

# Any questions?

---

# Quick recap

- Step 1: talk to people
- Step 2: get it to run
- Step 3: test the important bits
- Step 4: improve
