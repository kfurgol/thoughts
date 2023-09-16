---
layout: post
title:  "devlog: MVP deployed... and that's it."
date:   2023-09-16 23:21:00 +0200
categories: devlog
---

## Algoblaze

Due to a lack of better ideas, I've decided to start working on an algorithm and data structures learning platform.
Finally, I've deployed an MVP.

This MVP allows users to learn 9 data structures and 9 algorithms using Golang.
There is a written tutorial, where the user is supposed to implement a given algorithm or data structure. Then, the user code is then verified by the code-running engine.

You can check it here: [Algoblaze](https://algoblaze.com).

## Development

I was really demotivated to work on it for several reasons:
- I didn't like that idea: mindless grind just to get into high jobs, and I think these algo learning platforms eventually lead to that,
- Overwhelmed with the work to do,
- Learning new things is hard - I did not know some of the tools from the tech stack that I've chosen,
- It was summer, not the best time to work intensely,
- and many others.

I was really close to dropping the whole project completely (we've all been there), but I've decided to push and at least deploy the MVP.
And after 2.5 months, it is up and running.

## Tech stack

To develop this app I've used:
- Golang for backend service,
- PostgreSQL database (deployed on Supabase),
- React and MaterialUI for frontend service,
- 3rd party auth service (Supabase)
- Docker

For assets:
- undraw.co
- logo.com

For deployment:
- fly.io

## Architecture
There are 5 main components of the app:
1. Frontend
2. Backend
3. Database
4. Auth service
5. Code runner

![image](/assets/images/algoblaze.drawio.png)

Main flow:
1. User logs in via login and password, or Github, or Google account.
2. The user navigates to the algorithm or data structures list (loaded by the call to the backend service which retrieves it from DB - these are cashed on the frontend side).
3. By clicking on one item from the list, the user is navigated to the "Learn" page.
3. The learn page is a screen split in two
    - On the left side, there is a code editor where the user writes his solution. At the bottom of the page, there is a submit button and an output text box
    - On the right side, the user can switch between a text tutorial and a code editor with the correct answer.
4. When a user sends his code, the following happens:
    - User code is being sent to the backend,
    - Backend service starts a Docker container, which has a file with unit tests for each algorithm and data structure on the list,
    - The user code is run against the unit tests,
    - The output from the container is passed back as an output
5. The frontend app receives the output from tests and shows the appropriate message on success, failure, errors, etc.

## Problems
1. The platform lacks functionalities
    - I was thinking about incorporating spaced repetition into learning these algorithms. What I wanted to do with this platform, was to teach ALGORITHMS AND DATA STRUCTURES, not how to pass FAANG interview questions.
    - User statistics - how many times given algo was solved etc.
2. Low amount of content.
3. It's slow - running docker containers for each test is time-consuming.
4. No business model - Some of the not implemented functionalities I wanted to be paid.
5. UI is very basic
6. No tests, code's a mess

## What have I learned
1. You can deploy MVP of a web app for free (almost) - I've used fly.io, and to deploy docker containers I was asked to provide a credit card or buy some of their funds. I've decided to buy $25 of the funds to have peace of mind.
2. Frontend is not so easy, and React is an OK framework - lots of materials to be found online
3. PLAN your MVP and functionalities BEFORE you start writing a line of code. It will grow enormously during the development because as a creative mind, you'll get a lot of ideas (which may not be what users will want). So write an MVP plan and stick to it.
4. The simpler and more boring technology, the better.
5. FINALLY I'VE DELIVERED SOMETHING!

## Final words
During the time of development, I've read one book [Intercom on Starting up](https://www.goodreads.com/book/show/34908337-intercom-on-starting-up), and the second one that I am still reading [Zero To Sold](https://www.goodreads.com/book/show/54323859-zero-to-sold).
In one of them (I'm not sure which) the author speaks about Product-Founder fit. When I realized that in fact, I hate the idea of this algorithm and data structures learning platforms, I knew that I would drop the project. Yet still, I wanted finally to deliver SOMETHING, because I've always dropped the projects after one or two weeks.
Well, it will only get better from now on. 
