+++
menus = 'main'
date = '2025-02-16T11:07:52+01:00'
draft = false
title = 'Projects'
+++

# Projects

If I had to reduce my work up until this point to only 3 significant projects, I would select those 3. In this page you will learn about 1 personal project, 1 work project and one university project. I think these projects highlight my skills the best, as they account for most of my time spend developing during my engineering degree.

## 1 personal project: Thinker

Thinker is an application I co-founded with 2 software engineering students from [Epita](https://www.epita.fr/en/). The goal is to provide the user with quizzes on various subjects, that he can use to learn new things, improve his general knowledge or practice concepts he already knows. Quizzes are served to the user in an infinite vertical scrolling list, much like videos on [Tiktok](https://www.tiktok.com) or [Instagram Reels](https://www.instagram.com). Quizzes from the user's feed come from personalized recommandations, based on the user's following and quiz viewing habits. Thinker also aims to be a social network, where users can search and follow each other's profiles.

Thinker is currently in active development, and we are working towards releasing a functional v1 in 2025.

![2 screenshots of the thinker application](/thinker.png)

### Overview of the thinker application

#### Thinker tech stack

Thinker comes in the form of a cross platform (Android+IOS) mobile application, and these are some of the technologies we are using:

- [React native](https://reactnative.dev/) for the frontend, with the [Expo](https://expo.dev/) framework and [Typescript](https://www.typescriptlang.org/) for type checking.
- [Python](https://www.python.org/) for the backend, with the [FastAPI](https://fastapi.tiangolo.com/) framework.
- [Postgres](https://www.postgresql.org/) and [Qdrant](https://qdrant.tech/) for our databases
- [Alembic](https://alembic.sqlalchemy.org/en/latest/) for database migrations
- [Keycloak](https://www.keycloak.org/) for authentication
- [Kubernetes](https://kubernetes.io/) and [Docker](https://www.docker.com/) for deployments
- [Nginx](https://nginx.org/) for load balancing
- [Kafka](https://kafka.apache.org/) for handling frequent user events such as quiz interactions.

We also use [Figma](https://figma.com) to design all our UI's before implementing them, and maintain a large Figma file containing the whole Thinker design system.

#### System design

We decided to adopt a microservice architecture, so that we could easily split the different core functionalities in different repositories, and individually test parts of our backend. While it provides some overhead when setting up the backend, microservices streamline collaboration and allow for better separation of concerns (in my opinion).

We have 6 services:

- A user service, handling user authentication and information.
- A quiz service, handling all information related to quizzes. This includes quiz contents, interactions on quizzes such as views, likes...
- A generation service, used periodically to generate quizzes by using LLM API's such as the [OpenAI API](https://platform.openai.com). Generating quizzes solves the problem of initial content in the app, by allowing for mass generation of content on various subjects, whilst waiting for users to generate more content.
- An embedding service, used to store vector embeddings of quizzes and users in a [Qdrant](https://qdrant.tech/) database, which will then be used by the recommendation algorithm.
- A feed service, responsible for using the quiz and user embeddings to generate lists of quizzes ('feeds') that match the user's preferences.
- A notification service, handling push notifications for IOS and Android clients.

#### Deployment

As you can see with the tech stack, we focus on well-established, open source technologies, and the same goes when deploying the app. We recognize the power of modern cloud infrastructures like AWS or GCP, but we also want to avoid vendor lock-in, and want absolute control over our infrastructe. Currently, we are hosting the thinker
backend on a rented bare-metal server, that we use for development. When we hit v1, we will probably move to a cloud platform, however we will focus on leveraging only the basic compute services (e.g. EC2 in the case of AWS). While this approach certainly comes with strong tradeoffs, such as productivity and maintainability, we believe the advantages it provides regarding control and cost-reduction are still worth it. Handling the deployment of such a complex infrastructure from start to finish is also a good way to gain valuable DevOps knowledge.

#### Collaboration, standards and code quality

As a team of three developers, we explored multiple options regarding collaboration and code standards. We use the Kanban method to organize and plan work, and special emphasis is put on code quality and maintainability. Every change to the codebase is carefully reviewed by at least one other team member, and changes must always solve previously opened tickets in the Kanban board. All code must pass quality and style pipelines before merge, which include at least format and lint checks, and unit tests for the most critical areas.

Iterating fast is one of our objectives, however we still put a lot of focus on code quality and documentation, to ensure the project's maintainability as it grows.

### Personal contributions

As a cofounder and one the three developers for the thinker application, I was personnally responsible for:

- The react-native mobile application codebase
- The maintenance of the main Figma design file, that serves as the reference for all UI implementations.

I also made (and continue to make) significant contributions to the application's backend, most notably in the Quiz and User services.
I also introduced CI/CD pipelines to enforce code standards in multiple services, as well as in the frontend.

To sum up, I would define myself as a Fullstack engineer for this project, with an emphasis on frontend and UI/UX work.

## 1 work project: Scambio

Scambio is an R&D project at Orange, on which I've worked on for 6 months as a full-stack software engineering intern. Scambio (which translates to "exchange" in italian) is an online payment platform where businesses can generate QR Codes with the app that can be scanned by customers in order to initiate a payment operation. Customers don't need to have any application other than a web browser on their device, and the QR Code generated by the app can be printed on posters and used by multiple people multiple times. For this project, Orange partened with a startup called [Fintecture](https://www.fintecture.com), which provided a secure payment API using the latest European payment directives.

### Scambio tech stack

With Scambio being a relatively new project handled by a small team, we had the freedom to pick some more modern technologies to build the application. The app used:

- [Flutter](https://flutter.dev) for the frontend, in order to provide a cross platform (Android/IOS) application.
- [Go](https://go.dev) for the backend, with the [Gin Web Framework](https://gin-gonic.com)
- [Openshift](https://www.redhat.com/en/technologies/cloud-computing/openshift) and [Docker](https://www.docker.com) for deployments (self hosted on company infrastructure)
- [MongoDB](https://www.mongodb.com) for the database

We also used [Figma](https://www.figma.com) for UI/UX design and designer/developer communication.

![A screenshot of the login page for the scambio application](/scambio.png)

### Personal contributions

As a fullstack software engineering intern, I worked on both the frontend and backend of the application. I was heavily involved in a full rewrite of the app's UI, to comply to new UI guidelines within the Orange organisation. I also made numerous contributions to the backend and documentation for the application, and helped on some of the UI/UX decisions.

This internship was my first real work experience as a developer, and I learned a lot there about code quality, developer collaboration and secure API design. This was also the opportunity to learn how to use a NoSQL database, as well as 2 new languages which I hadn't done before: Dart and Go.

## 1 university project: RCube

RCube is an android application I wrote for my android developement class. The app allows it's users to time themselves when solving Rubik's Cube, on the model of apps like [Twisty Timer](https://play.google.com/store/apps/details?id=com.aricneto.twistytimer&hl=en&pli=1) or [CSTimer](https://cstimer.net). It provides official cube scrambles with scramble previews, stores times locally, and calculates interesting stats for people versed into [Speedcubing](https://en.wikipedia.org/wiki/Speedcubing).

The application is written in [Kotlin](https://kotlinlang.org) and targets Android SDK versions 35 and up. It uses the [Jetpack Compose framework](https://developer.android.com/compose) and follows the latest [Material 3 guidelines](https://m3.material.io), including [Material You](https://m3.material.io/blog/announcing-material-you). RCube stores it's data locally in the already available [SQLite](https://www.sqlite.org) databases on android devices. The app also follows the android guidelines regarding project structure and local data handling, with the [Room](https://developer.android.com/training/data-storage/room) library.

RCube is fully open-source and you can check it's source code on [GitHub](https://github.com/raphaelweis/RCube/).

![A screenshot of the timer screen for the RCube app](/rcube.png)
