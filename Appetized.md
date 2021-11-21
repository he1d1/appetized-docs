# Appetized

[TOC]

## Analysis

Lots of young people aren't cooking for themselves. Home cooking has many benefits [^Citation needed] like `//TODO`. A
possible reason young adults aren't cooking for themselves is that there isn't an online repository that is engaging and
fun. Progressive Web Apps (PWAs) are suited to recipes because they can deploy to app stores and the web with the same
code-base [^Citation needed]. A sensible architecture for the project would be the client-server model. A centralised
system would ensure recipes are up-to-date. Additionally, I can more easily add authentication and social features.

### Target Audience

People aged 16-24 are `//TODO`% less likely to cook for themselves [^ Citation needed], this is because `//TODO`.

### Existing Solutions

#### Cookbooks

Recipe books are the traditional way of getting recipes. They are often written informally and have images and other
aids to help with cooking the recipes. I think people use them because they are beginner-friendly, and the ingredients
and utensils needed are accessible. They also contain a range of information about each recipe, such as nutritional
information or how long it takes to prep and cook that helps the reader pick out recipes.

An ideal recipe website would have all the strengths of a cookbook and have the convenience of being accessible anywhere
and have a greater variety of recipes. A recipe book usually has a theme, so maybe I could add a way of saving recipes
into organised cookbooks for offline usage.

A disadvantage of cookbooks is that you need to buy them or take them out from a library. They tend to be pretty pricey,
with them costing around £5 to £20.

#### Social Media

`//TODO`% of people get their recipes from social media platforms like Facebook or Instagram.

##### Instagram

The way to share recipes on Instagram is via video. However, the video player is limited in functionality, making it a
frustrating experience when cooking. The length of videos on Instagram is between 3 and 60 seconds [^ Citation needed],
which means that intricate recipes are usually rushed through and missing vital details. There is also no way to pause
or rewind, which means if you missed something, you have to start the video again.

##### Facebook

Some people also get their recipes from Facebook recipe pages. These pages usually post images or videos like those on
Instagram linking to an external recipe website that they run for more detailed instructions. However, there isn’t a way
to save or pin a recipe for later. Saving is an essential feature because it can be hard to find a post again.

---

I think the main reason that people get their recipes off of social media is that most mobile users prefer using an app
over using a web browser. [^ Citation needed]

#### Recipe Blogs

`//TODO fix grammar`

Recipe blogs are another popular way to get recipes, they are usually ran by a chef and have just their recipes. These
are great for the same reasons as a cookbook, having a personal touch.

A lot of blogs are built with a [WYSIWYG][wysiwyg] (_What You See Is What You Get_, pronounced: “wiz-e-wig”) website
editor, these can be good for beginners because they are easy to use, and you can make a website relatively fast. There
are however, a large number of drawbacks to these editors. Primarily, WYSIWYG sites often have terrible performance, SEO
and layout optimisation on mobile. The slow speed results from sharing the server with a ton of other websites and the
generated code itself being poorly optimised. WYSIWYG editors also tend to not encourage mobile-first design, making the
user build the desktop site, and then rearrange the elements to better fit mobile. Most of the time, people using
WYSIWYG editors won't have learned about UI best practises, resulting in a bad user experience, especially on mobile.
Due to the poor performance and layout, the SEO on generated sites is already going to be low, but there also isn’t a
way to implement advanced SEO. Google Search allows websites to give [structured data][structured data] which allows web
developers to have their sites appear in Google’s Rich results, this is an important way to drive traffic to a recipe
blog. However, on website builders, there isn’t a way to automatically have this data appear on your sites. On Wix, you
have to individually add structured data for each page even though its already in the websites CMS, this is an obscure
feature and most recipe bloggers won't pay attention to it.

Building a recipe blog from scratch can be an expensive and time-consuming process and isn’t accessible to a lot of
people. This could be solved with a recipe sharing website that is focused on great SEO and ease of use.

### Solution

Appetized will be composed of two applications, `appetized-client` and `appetized-server`. Appetized server will have a
database containing recipes, user information, such as login details, and saved recipes. This database will be able to
be interacted with via an API that I will implement. The client will provide users a GUI and will request data from the
API.

Appetized will take from a number of features from existing solutions. Instagram's feed page shows all posts from
followed users ordered by upload date, this ensures that you won't see repeated recipes mixed in with new ones and is
easy to implement. `//TODO add more things that the solution is insired by`

#### Limitations

There are a few limitations with this solution however:

Firstly, a platform like this would have to be moderated by hand, as time constraints mean that there won't be time to
create an automated system that could classify the content uploaded and make sure that it is recipes... _for food_. Some
websites that are primarily hosting user generated content struggle to keep the things that their users upload are
firstly, on topic and secondly (and most importantly) not illegal.

Secondly, I don’t plan to implement a recommendation system, these are incredibly hard to implement, especially on a
brand-new platform with no data.

### Features

For Appetized to feel complete, it must do the following:

- Host user uploaded recipes, with an on-site method of creating them.
- Have social features, like following other users and saving recipes.
- Have a secure authentication system.
- Have a way of finding user uploaded recipes.

### Requirements

To be able to access the official version Appetized, all a user will need is a device capable of running a modern web
browser, or installing an .apk or .ipa file. The user will also require an internet connection at least once to download
the content from the website and save it. Saved recipes will be stored locally, so you will not need an internet
connection to view it.

I plan for Appetized to be open-source, so users can run their own instance of `appetized-server` or `appetized-client`.
Users planning to host `appetized-server` will need a computer that is capable of running Node.js version 12 and the
latest version of PostgreSQL.

To run a local version of the client, a user will just need a computer capable of running Node.js version 12, however,
if a user’s computer couldn’t run Node.js, they could manually send queries to the API.

### Success Criteria

|  ID   | Description                                                         | Server                                                                                                            | Client                                                                                                    | Priority |
| :---: | :------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | -------- |
| `id1` | User can upload & edit recipes.                                     | Will need to be capable of receiving a recipe and storing it in a database.                                       | Will need a recipe creation/editing page.                                                                 | High     |
| `id2` | User can view recipes.                                              | Will need to be able to receive requests for a specific recipes and respond.                                      | Will need a page for each recipe that requests it from the server and then displays it.                   | High     |
| `id3` | User can create an account.                                         | Will need to be able to receive account creation requests.                                                        | Will need a registration page.                                                                            | High     |
| `id4` | User can log into their account.                                    | Will need to be able to authenticate a user based on their email and password.                                    | Will need a login page.                                                                                   | High     |
| `id5` | Users stay logged in.                                               | Will need to be able to issue a user a cookie and check this cookie with each request to see if it is authorised. | Will need to be able to receive cookies.                                                                  | High     |
| `id6` | Users will be able to recover a lost account with a recovery email. | Will need to be capable of sending an email that contains a password recovery link.                               | Will need a password reset form.                                                                          | Low      |
| `id7` | Users will be able to save a recipe.                                | Will need to be capable of receiving a recipe save request and store this in a database table.                    | Will need to be able to display saved recipes in a list. Will need to have a button to save recipes with. | High     |
| `id8` | Saved recipes will be stored locally.                               | N/A                                                                                                               | Saved recipes need to be stored in local storage.                                                         | Low      |
| `id9` | Users will be able to follow another user.                          | Will need to be capable of receiving follow and unfollow request.                                                 | Will need a page for following and followers as well as a follow/unfollow button for each user.           | High     |

## Design

Appetized will be made up of two applications, a client and a server.

### Server

The server will be built up of four different sections. There will be a database, which will contain all of the site’s data, except images, and will not be publicly accessible. There will also be a cloud storage bucket, which will host all of the images. Another section will be an object-relational mapping (ORM) tool, which will be used to read and write from the database with objects rather than a database query language like SQL. There will also be an application programming interface (API) which will allow the client to make requests to the server. 

I think this platform will need authentication so users can have the correct authorisation to edit the site’s data. Without authentication, anyone could delete other people’s recipes. I am going to implement authentication with JSON Web Tokens (JWT). A JWT is a token made up of three parts, a header, a payload and a signature. The header contains information about the JWT. The payload contains some information that in Appetized case will be a user’s ID. The payload is encrypted with a private key and, can be verified using the signature.

#### API

The application programming interface (API) will receive and respond to requests in the GraphQL query language. GraphQL is an alternative to the standard way of implementing an API, REST. When building a large application, like Appetized, REST has a number of downsides. REST works by having a different endpoint for each request. For example, to get a recipe i might go to `www.appetized.developer.lu/recipe/293478`, this will return all of the information about the recipe `293478`. The main problem with this approach is if I only needed a small section of the response, I will still have to download all of this extra data that is going to go unused. Additionally, If I wanted information that wasn’t returned at that endpoint, I would have to fetch data from another endpoint. As a result, REST APIs use a lot of unnecessary bandwidth. A GraphQL server uses a single endpoint, however, you can request specific data. This will keep the number of requests and their sizes down, which will help the server and the client perform better.

##### Type Definitions

GraphQL has a type system with a very limited number of built in types (`String`,  `ID`, `Boolean`, `Float` and `Int`).  I am planning to implement my own types so the data that can be requested is more organised. 

The `User` type will contain publicly accessible data about a user and the content they have uploaded onto the site.  

| Field Name        | Type       | Description                                                  |
| :---------------- | :--------- | :----------------------------------------------------------- |
| `id`              | `ID!`      | A unique identifier for a user.                              |
| `name`            | `String!`  | The persons full name.                                       |
| `username`        | `String!`  | A unique and human readable name to identify a user.         |
| `joinDate`        | `Date!`    | The date a user created their account (Greenwich mean time). |
| `editDate`        | `Date`     | The date a user last edited any account details (Greenwich mean time). |
| `profilePicture`  | `Image`    | An image to represent a user.                                |
| `uploadedRecipes` | `[Recipe]` | All of the recipes a user has uploaded.                      |
| `following`       | `[User]`   | All of the accounts a user is following.                     |
| `followers`       | `[User]`   | All of the accounts that are following a user.               |
| `savedRecipes`    | `[Recipe]` | All of the recipes a user has saved.                         |

The `Recipe` type will contain the instructions of a recipe and some metadata about it. It is based off of the [Schema.org recipe type][recipe type] so it can be used easily as [structured data][]. This allows it to show up in rich search results.

| Field Name     | Type                        | Description                                         |
| -------------- | --------------------------- | --------------------------------------------------- |
| `id`           | `ID!`                       | A unique identifier for a recipe.                   |
| `image`        | `Image!`                    | An image of the completed recipe.                   |
| `name`         | `String!`                   | The title of the recipe.                            |
| `author`       | `User!`                     | The user who posted the recipe.                     |
| `rating`       | `Rating`                    | A rating out of 5 of the quality of the recipe.     |
| `prepTime`     | `Int`                       | How many minutes it takes to prepare the recipe.    |
| `cookTime`     | `Int`                       | How many minutes the dish will spend cooking.       |
| `uploadDate`   | `Date`                      | The date the recipe was created.                    |
| `editDate`     | `Date`                      | The date the recipe was last edited.                |
| `description`  | `String`                    | A short description of the dish.                    |
| `keywords`     | `[String]`                  | A list of alternate words that describe the recipe. |
| `calories`     | `Int`                       | How many calories are in the recipe.                |
| `cuisine`      | `String`                    | The region the dish is connected to.                |
| `ingredients`  | `[QuantitativeIngredient!]` | A list of ingredients with their quantity.          |
| `instructions` | `[Instruction!]`            | A list of steps.                                    |
| `yeild`        | `QuantitativeIngredient`    | How much the recipe will make.                      |
| `savedBy`      | `[User]`                    | Who has saved the recipe.                           |

The `Image` type will contain the URL to an image and some information about it.

| Field Name   | Type      | Description                                              |
| ------------ | --------- | -------------------------------------------------------- |
| `url`        | `String!` | The URL of where the image is stored.                    |
| `alt`        | `String`  | A description of the images for users of screen readers. |
| `author`     | `User!`   | The user who uploaded the image.                         |
| `uploadDate` | `Date!`   | The date that the image was uploaded to the site.        |

`Rating` will be a type that gives information about the overall rating of a recipe.

| Field Name     | Type      | Description                                    |
| -------------- | --------- | ---------------------------------------------- |
| `totalRatings` | `Int!`    | The number of ratings that have been received. |
| `stars`        | `Float!`  | The overall rating of the recipe.              |
| `ratedBy`      | `[User!]` | The users who have left a rating.              |

The `Date` type will give a date and time in Greenwich Mean Time.

| Field Name | Type    |
| ---------- | ------- |
| `year`     | `Int!`  |
| `month`    | `Int!`  |
| `day`      | `Int!`  |
| `hour`     | `Int`   |
| `minute`   | `Int`   |
| `second`   | `Float` |

 The `QuantitativeIngredient` type will have an ingredient, how much of it and the unit.

| Field Name   | Type          | Description                                                  |
| ------------ | ------------- | ------------------------------------------------------------ |
| `ingredient` | `Ingredient!` | The ingredient itself.                                       |
| `amount`     | `Float!`      | The amount of the ingredient.                                |
| `unit`       | `String!`     | The unit the ingredient is measured in. (For example “litre”) |

The `Ingredient` type will contain the name of the ingredient and an array of user submitted images of that ingredient.

| Field Name | Type       |
| ---------- | ---------- |
| `name`     | `String!`  |
| `images`   | `[Image!]` |

The `Instruction` type will be a union between the `Step` and `StepSection` types.

The `Step` type is going to be contain some data about a step and will either contain a `Direction` or a `Tip`

| Field Name | Type       | Description                        |
| ---------- | ---------- | ---------------------------------- |
| `name`     | `String`   | The title of the step              |
| `text`     | `String!`  | The actual instruction             |
| `url`      | `String`   | The URL of the step.               |
| `image`    | `Image`    | An image of the step.              |
| `tip`      | `Boolean!` | If the step is a tip or direction. |

The `StepSection` type that contains several steps.

| Field Name | Type      |
| ---------- | --------- |
| `name`     | `String!` |
| `steps`    | `[Step!]` |

##### Resolvers 

In GraphQL there are three types of request, mutations, queries and subscriptions. A mutation is a request that will modify data and return a value. Appetized’s mutations will cause a change in the database. Queries are for reading data. Subscriptions are like queries, but the data they return can be changed over time. There aren’t any uses for subscriptions in Appetized however, so just queries and mutations will be used. 

Mutations and queries are written as functions called resolvers. The value returned by the resolver is what is sent as a response to the caller. Resolvers take 4 arguments:

- `obj` The parent object. For example, if someone requested a list recipes and their authors, the recipes would be what is stored in `obj`
- `args` The arguments passed into the request. For example the mutation: `login(email:  "email@lewie.me", password: "aoeu")`'s arguments would be email and password. 
- `context` is a object that is provided to a resolver and holds information such as the user that is logged in. On Appetized, this will an object containing the user Id, from the payload of the decoded JWT.
- `info` Contains information about the request.

Here is a pseudo-code algorithm for how the context will be set for resolvers (If I use Apollo Server and TypeORM and JavaScript). 

```typescript
// The context is set in the constructor for the GraphQL server.
const server = new ApolloServer({
	typeDefs,
	resolvers,
	context: ({ req, res }) => {
		// The context that will be returned if a user Id is not found.
		const context = {
			req: req,
			res: res,
			id: null,
		};

		// req is an object which contains information about the request made to the server.
		const accessToken = req.cookies['accessToken'];
		const refreshToken = req.cookies['refreshToken'];

		// If the user has an access token.
		if (accessToken !== null) {
			try {
				// Gets the user's id and how many times they have changed their password.
				const { id, passwordChanges } = jwt.verify(
					accessToken,
					process.env.ACCESS_TOKEN,
				);
                // If password has changed since the user has last logged in.
				if (passwordChanges !== db.User.passwordChanges) {
					return context;
				}
				context.user = id;
				return context;
			} catch (err) {
				//If verification fails, it will return the context with a null id.
				return context;
			}
		} else if (refreshToken !== null) {
			try {
				// Gets the user's id and how many times they have changed their password.
				const { id, passwordChanges } = jwt.verify(
					refresh,
					process.env.ACCESS_TOKEN,
				);
                // If password has changed since the user has last logged in.
				if (passwordChanges !== db.User.passwordChanges) {
					return context;
				}
				// Creates new access token.
				res.cookies(
					'accessToken',
					sign(
						{ userId: user.id, count: count },
						process.env.ACCESS_TOKEN,
					),
                    { expiresIn: '1h' },
				);
				// Creates new refresh token.
				res.cookies(
					'refreshToken',
					sign(
						{ userId: user.id, count: count },
						process.env.REFRESH_TOKEN,
					),
                    { expiresIn: '30d' },
				);
                // returns the context with user Id
				context.user = id;
				return context;
			} catch (err) {
				//If verification fails, it will return the context with a null id.
				return context;
			}
		}
		//If the user has no access or refresh token, context with a null id wil be ruterned.
		return context;
	},
});
```

There will be a very large number of revolvers for Appetized, and they will follow a similar format, so here is one example of what one will look like. Here is what the `login` mutation might look like:

```typescript
export default {
	Mutation: {
		login: async (_, { email, password }, { req, res, id }) => {
			// If user is already logged in, return true;
			if (id) return true;
			// Find the password hash of the user attempting to log in.
			const { passwordHash } =
				(await db.User.findOne({ email: email })) ?? '';
			// Check if password is correct.
			await argon2
				.verify(passwordHash, password)
				.then((passwordCorrect) => {
					if (passwordCorrect) {
						// Creates new access token.
						res.cookies(
							'accessToken',
							sign(
								{ userId: user.id, count: count },
								process.env.ACCESS_TOKEN,
							),
							{ expiresIn: '1h' },
						);
						// Creates new refresh token.
						res.cookies(
							'refreshToken',
							sign(
								{ userId: user.id, count: count },
								process.env.REFRESH_TOKEN,
							),
							{ expiresIn: '30d' },
						);
					}
					// Return if the password is correct.
					return passwordCorrect;
				});
		},
	},
};
```

#### Images

Images will not be stored on the server, instead they will be stored on a cloud storage bucket. Their URL will be stored in the database as well as its metadata. Most cloud providers have their own proprietary library to upload files. This can cause vendor lock in, as if you need to change provider, you will need to edit the code you have written. 

I am going to use AWS primarily because of [Rekognition][amazon rekognition], which I can use for content moderation. They also have free tiers for their cloud storage and lambda functions.

## Sprint 1

The first sprint will be dedicated to setting up the backend and implementing authentication. I have chosen to use Apollo Server and TypeORM in this stage of the project. I plan to implement five resolvers in this sprint, `login`, `logout`, `addUser`, `editUser`, and `deleteUser`.

Firstly, I need to write write the entry point for the backend of the project, `app.ts`. It will be responsible for configuring and starting up different parts of the backend.

```ts
import resolvers from "./resolvers";
import typeDefs from "./typeDefs";
import { PrismaClient } from "@prisma/client";
import { config } from "dotenv";
import { startApolloServer } from "./server";
import { Tedis } from "tedis";
import nodemailer from "nodemailer";
import { SESClientConfig } from "@aws-sdk/client-ses";

const aws = require("@aws-sdk/client-ses");

// Sets .env config as default.
config();

// Connects to database.
export const prisma = new PrismaClient();

// Configures AWS SES.
let ses = new aws.SES({
  region: "us-east-2",
  endpoint: "https://email.us-east-2.amazonaws.com",
  credentials: {
    accessKeyId: process.env.AWS_ACCESS_KEY_ID,
    secretAccessKey: process.env.AWS_SECRET_ACCESS_KEY,
  },
} as SESClientConfig);

// Creates nodemailer transport.
export let transporter = nodemailer.createTransport({
  SES: {
    ses,
    aws,
  },
} as any);

// Starts Redis server.
export const redis = new Tedis({
  host: process.env.REDIS_HOST ?? "localhost",
  port: parseInt(process.env.REDIS_PORT ?? "6379"),
});

// Starts server.
startApolloServer(typeDefs, resolvers).then((server) => {
  console.log(
    `${process.env.NODE_ENV?.charAt(
      0
    ).toUpperCase()}${process.env.NODE_ENV?.slice(
      1
    )} server ready.\nGraphQL explorer at: http://localhost:4000${
      server.graphqlPath
    }`
  );
});
```

The line `config()` gives the package `dotenv` the default configuration. `dotenv` loads environmental variables. In this project, they will be stored in a file called `.env`, which will contain any information that is specific to the environment that the application is running in, for example, the password to the database will be different on each instance of the server so this will be fed into the server via a `.env` file. 

`export const prisma = new PrismaClient()` creates a new instance of [Prisma][prisma], the ORM I have decided to use. The `export` keyword allows other files in the project to access it. 

`let ses = new aws.SES({...})` creates a client for the [Amazon Simple Email Service][SES]. It gets an object passed into the constructor containing configuration. The object contains the region, endpoint and AWS credentials.

```ts
export let transporter = nodemailer.createTransport({
  SES: {
    ses,
    aws,
  },
} as any);
```

Creates a wrapper around the SES client using `nodemailer`. This wrapper will automatically create MIME formatted emails. It is exported so it can be accessed by resolvers to send emails.

```ts
// Starts Redis server.
export const redis = new Tedis({
  host: process.env.REDIS_HOST ?? "localhost",
  port: parseInt(process.env.REDIS_PORT ?? "6379"),
});
```

Starts the Redis client, this is used to store the tokens used in email verification, and may be used to store session tokens. It is exported to be used in other parts of the server.

```ts
// Starts Apollo server.
startApolloServer(typeDefs, resolvers).then((server) => {
  // Console message.
  console.log(
    `${process.env.NODE_ENV?.charAt(
      0
    ).toUpperCase()}${process.env.NODE_ENV?.slice(
      1
    )} server ready.\nGraphQL explorer at: http://localhost:4000${
      server.graphqlPath
    }`
  );
});
```

Calls a function I have written that starts [Express][express] and [Apollo Server][Apollo Server], then, prints a message to the console. 

```bash
Development server ready.
GraphQL explorer at: http://localhost:4000/
```

The first word, i.e. the environment that the server is running in. This will be either “Development”, or “Production”. These environments have a few differences, for example, cookies will behave differently when in development so they can be accessed in any domain, however in production, they will need to be only accessible by the client for security reasons.

The next line gives the URL to a GraphQL explorer, where I test the server.

![GraphQL Explorer](https://github.com/hiluw/appetized-docs/raw/main/assets/GraphQL%20explorer.png)

Here is the code for `startApolloServer()`

```ts
// Stars Apollo Server.
import { DocumentNode } from "graphql";
import express from "express";
import http from "http";
import cookieParser from "cookie-parser";
import { ApolloServer } from "apollo-server-express";
import { ApolloServerPluginDrainHttpServer } from "apollo-server-core";
import { context } from "./context";
import { prisma, redis } from "./app";

export async function startApolloServer(
  typeDefs: DocumentNode,
  resolvers: any
) {
  // Required logic for integrating with Express.
  const app = express();
  const httpServer = http.createServer(app);

  // This creates req.cookies
  app.use(cookieParser());

  app.use((res, req, next) => {
    // This is required for Apollo Server to work with Express.
    // @ts-ignore
    req.context = {};
    next();
  });

  // Email confirmation
  app.use("/verify/:token", async ({ params: { token } }, _, next) => {
    const id: string = (await redis.get(token)) as string;

    if (!id) {
      return next();
    }

    await redis.del(token);

    console.log(id);

    await prisma.user.update({
      where: { id },
      data: {
        emailVerified: true,
      },
    });

    return next();
  });

  // Same ApolloServer initialization as before, plus the drain plugin.
  const server = new ApolloServer({
    typeDefs: typeDefs,
    resolvers: resolvers,
    plugins: [ApolloServerPluginDrainHttpServer({ httpServer })],
    context,
  });

  // More required logic for integrating with Express
  await server.start();
  server.applyMiddleware({
    app,
    path: "/",
    cors: {
      origin: "https://studio.apollographql.com",
      credentials: true,
    },
  });

  // Modified server startup
  await httpServer.listen({ port: 4000 });

  return server;
}

```

This function firstly starts express, and then creates a HTTP server. Then, the `cookie-parser` middleware is registered and the context object is set to null. Next the route for email verification is created. When a user visits the `/verify/token` path, the value of token is checked in Redis, and then the user associated with that token will have their email verified. After that, Apollo Server is started and the `context()` function I created is passed into the constructor. Finally, the server is started, and the the server starts listening at port 4000.

The context function checks weather a user is authenticated and handles their cookies, returning their Id if they are authenticated.

```ts
export function context({ req, res }: any): Object {
  try {
    const { id, logouts } = jwt.verify(
      req.cookies["accessToken"] ?? null,
      process.env.ACCESS_TOKEN as string
    ) as any;
    return { req, res, id, logouts };
  } catch (e) {
    try {
      const { id, logouts } = jwt.verify(
        req.cookies["refreshToken"] ?? null,
        process.env.REFRESH_TOKEN as string
      ) as any;
      cookies(res, id, logouts);
      return { req, res, id, logouts };
    } catch (e) {
      return { req, res, id: null, logouts: null };
    }
  }
}
```

If the user needs a new set of access and refresh tokens, the `cookies()` function is called. 

```ts
import { Secret, sign } from "jsonwebtoken";new 
import { CookieOptions } from "express";

export function cookies(res: any, id: string, logouts: number) {
  res.cookie(
    "accessToken",
    sign({ id: id, logouts: logouts }, process.env.ACCESS_TOKEN as Secret),
    {
      expiresIn: "1h",
      httpOnly: true,
      sameSite: process.env.NODE_ENV === "production" ? "lax" : "none",
      secure: true,
    } as CookieOptions
  );
  res.cookie(
    "refreshToken",
    sign({ userId: id, logouts: logouts }, process.env.REFRESH_TOKEN as Secret),
    {
      expiresIn: "30d",
      httpOnly: true,
      sameSite: process.env.NODE_ENV === "production" ? "lax" : "none",
      secure: true,
    } as CookieOptions
  );
}

```

`cookies()` issues the user with an access token and a refresh token. 

### Resolvers

The 5 resolvers I am going to implement this sprint are all going to be mutations.

Resolvers are imported in `server.ts` and passed to `startApolloServer()` as an object containing functions.

This object is made in the `resolvers.ts`, the functions it contains are located in different files.

```ts
import { login } from "./user/login";
import { logout } from "./user/logout";
import { addUser } from "./user/addUser";
import { editUser } from "./user/editUser";
import { deleteUser } from "./user/deleteUser";

export default {
  Query: {},
  Mutation: {
    addUser,
    deleteUser,
    editUser,
    login,
    logout
  },
};
```

Here is the resolver for logging in:

```ts
import { AuthenticationError, UserInputError } from "apollo-server-express";
import { prisma } from "../app";
import argon2 from "argon2";
import { cookies } from "../cookies";

export const login = async (
  _: any,
  { email, password }: any,
  { res, id }: any
) => {
  // An object that stores any validation errors that occur during the login process.
  const validationErrors: any = {};

  // Checks if user is already logged in.
  if (id) throw new AuthenticationError("Already logged in.");

  // Checks if user has entered an email.
  if (!email) validationErrors.email = "Email is required.";

  // Checks if user has entered a password.
  if (!password) validationErrors.password = "Password is required.";

  // Finds user in database from their email.
  const user = await prisma.user.findUnique({
    where: {
      email: email,
    },
  });

  // Throws validation errors
  if (Object.keys(validationErrors).length > 0) {
    throw new UserInputError("Failed to login due to user input.", {
      ...validationErrors,
    } as any);
  }
  // returns true if the user exists and their password is correct.
  if (user && (await argon2.verify(user.passwordHash, password))) {
    if (!user.emailVerified) {
      throw new AuthenticationError("Email not verified.");
    }
    // Creates new set of tokens.
    cookies(res, user.id, user.logouts);
    return {
      success: true,
      message: "Login successful.",
      code: 200,
    };
  } else {
    // Throws error if user does not exist or password is incorrect.
    throw new AuthenticationError("Incorrect email or password.");
  }
};

```

Here is the resolver for logging out: 

```ts
import { AuthenticationError } from "apollo-server-express";
import { prisma } from "../app";

export const logout = async (_: any, __: any, { res, id }: any) => {
  // Checks if user is already logged out.
  if (!id) throw new AuthenticationError("Not logged in.");

  // Clears the user's cookies.
  res.clearCookie("accessToken");
  res.clearCookie("refreshToken");

  // Increments the user's logouts.
  await prisma.user
    .update({
      where: {
        id: id,
      },
      data: {
        logouts: { increment: 1 },
      },
    })
    .catch(() => {
      throw Error("Failed to logout");
    });

  return {
    success: true,
    message: "Logout successful",
    code: 200,
  };
};
```

 Here is the resolver for registering a new account, please note that images will be implemented in a later sprint:

```ts
import { AuthenticationError, UserInputError } from "apollo-server-express";
import argon2 from "argon2";
import { prisma, redis, transporter } from "../app";
import { User } from "apollo-server-core/src/plugin/schemaReporting/operations";
import { v4 } from "uuid";

export const addUser = async (
  _: any,
  { email, user: { name, username, password }, image }: any,
  { id }: any
) => {
  // An object that stores any validation errors that occur while creating a user.
  const validationErrors: any = {};

  // Checks if a name was entered.
  if (!name) validationErrors.name = "Name is required.";

  // Checks if a username was entered.
  if (!username) validationErrors.username = "Username is required.";

  // Checks if a password was entered.
  if (!password) validationErrors.password = "Password is required.";

  // Checks if password is long enough
  if (password.length < 8)
    validationErrors.password = "Password must be at least 8 characters.";

  // Checks if password is short enough
  if (password.length > 128)
    validationErrors.password = "Password must be less than 128 characters.";

  // Checks if an email was entered.
  if (!email) validationErrors.email = "Email is required.";

  // Checks if an image was entered.
  if (image) {
    // Checks if the image is too big.
    if (image.imageBase64.length > 10 * 1000000) {
      validationErrors.image = "Image must be less than 10MB.";
    }
    // TODO implement images.
    validationErrors.image = "Images have not yet been implemented";
  }

  // Checks if already logged in.
  if (id) throw new AuthenticationError("Already logged in.");

  // Hashes the password.
  const passwordHash = await argon2.hash(password);

  // Creates a user in the database.
  const user =
    (await prisma.user
      .create({
        data: {
          email,
          username,
          name,
          passwordHash,
        },
      })
      // If the creation of the user fails.
      .catch(({ code, meta: { target } }) => {
        // P2002: Unique constraint violation.
        if (code == "P2002")
          // For each field with a unique constraint violation.
          target.forEach((err: string) => {
            // Set the error message for that field.
            validationErrors[err] = `${
              // Capitalize the first letter of the field name.\
              err.charAt(0).toUpperCase() + err.slice(1)
            } is already in use.`;
          });
      })) ?? ({} as User);

  // If there are any validation errors.
  if (Object.keys(validationErrors).length > 0) {
    throw new UserInputError("Failed to add account due to user input.", {
      ...validationErrors,
    } as any);
  }

  // Generates a uuid for the email verification and stores it in redis.
  const token = v4();
  await redis.set(token, user?.id);

  // Sends an email to the user with a verification link.
  await transporter.sendMail({
    from: `Appetized <no-reply@${process.env.EMAIL_URL}>`,
    to: email,
    subject: "Verify your email",
    html: `<a href="${
      process.env.SERVER_URL ?? "http://localhost:4000"
    }/verify/${token}">Verify your email</a>`,
  });

  // If the user was created successfully.
  return {
    success: true,
    message: "User created",
    code: 200,
  };
};

```

Here is the resolver for editing your account: 

```ts
import { AuthenticationError, UserInputError } from "apollo-server-express";
import { prisma } from "../app";

export const editUser = async (
  _: any,
  { name, username, image }: any,
  { id, logouts }: any
) => {
  // An object that stores any validation errors that occur while editing a user.
  const validationErrors: any = {};

  // If the user is not logged in.
  if (!id) throw new AuthenticationError("Already logged in.");

  // Checks if an image was entered.
  if (image) {
    // Checks if the image is too big.
    if (image.imageBase64.length > 10 * 1000000) {
      validationErrors.image = "Image must be less than 10MB.";
    }
    // TODO implement images.
    validationErrors.image = "Images have not yet been implemented";
  }

  const user: any = await prisma.user.findUnique({
    where: {
      id,
    },
    select: {
      id: true,
      name: true,
      username: true,
      logouts: true,
    },
  });

  console.log(user);

  if (user?.logouts !== logouts)
    throw new AuthenticationError("Session is expired.");

  // Check new username is different from old username.
  if (user?.username === username)
    validationErrors.username = "Username is already in use.";

  if (user?.name === name) validationErrors.name = "Name is already in use.";

  // If the creation of the user fails.
  await prisma.user
    .update({
      where: {
        id,
      },
      data: {
        name,
        username,
      },
    })
    // If updating the user fails
    .catch(({ code, meta: { target } }: any) => {
      // P2002: Unique constraint violation.
      if (code == "P2002")
        // For each field with a unique constraint violation.
        target.forEach((err: string) => {
          // Set the error message for that field.
          validationErrors[err] = `${
            // Capitalize the first letter of the field name.\
            err.charAt(0).toUpperCase() + err.slice(1)
          } is already in use.`;
        });
    });
  // If there are any validation errors.
  if (Object.keys(validationErrors).length > 0) {
    throw new UserInputError("Failed to add account due to user input.", {
      ...validationErrors,
    } as any);
  }

  // User edited successfully.
  return {
    success: true,
    message: "User edited",
    code: 200,
  };
};

```

Here is the resolver for deleting your account:

```ts
import { AuthenticationError } from "apollo-server-express";
import { prisma } from "../app";

export const deleteUser = async (
  _: any,
  __: any,
  { res, id, logouts }: any
) => {
  // If the user is not logged in.
  if (!id) throw new AuthenticationError("Not logged in.");

  const user: any = await prisma.user.findUnique({
    where: { id },
    select: { id: true, logouts: true },
  });

  if (!user || user?.logouts !== logouts)
    throw new AuthenticationError("Session is expired.");

  await prisma.user.delete({
    where: {
      id,
    },
  });

  // Clears the user's cookies.
  res.clearCookie("accessToken");
  res.clearCookie("refreshToken");

  return {
    success: true,
    message: "User deleted",
    code: 200,
  };
};

```

### Type Definitions

I have created the type definitions for the entire app, except for the resolvers, here they are:

```ts
import { gql } from "graphql-tag";

export default gql`
  type Recipe {
    id: ID!
    image: Image!
    name: String!
    author: User!
    rating: Rating
    prepTime: Int
    cookTime: Int
    uploadDate: Date
    editDate: Date
    description: String
    keywords: [String]
    calories: Int
    category: String
    cuisine: String
    ingredients: [QuantitativeIngredient!]
    instructions: [Instruction!]
    yield: QuantitativeIngredient
    savedBy: [User]
  }

  input RecipeInput {
    name: String!
    prepTime: Int
    cookTime: Int
    description: String
    keywords: [String]
    calories: Int
    category: String
    cuisine: String
  }

  type User {
    id: ID!
    name: String!
    username: String!
    joinDate: Date!
    editDate: Date
    profilePicture: Image
    uploadedRecipes: [Recipe]
    following: [User]
    followers: [User]
    savedRecipes: [Recipe]
  }

  input UserInput {
    name: String!
    username: String!
    password: String!
  }

  type Image {
    url: String!
    alt: String
    author: User!
    uploadDate: Date!
  }

  input ImageInput {
    imageBase64: String!
    alt: String
  }

  type Rating {
    totalRatings: Int!
    stars: Float!
    ratedBy: [User!]
  }

  input RatingInput {
    rating: Float!
  }

  type Date {
    year: Int!
    month: Int!
    day: Int!
    hour: Int
    minute: Int
    second: Float
  }

  input DateInput {
    year: Int!
    month: Int!
    day: Int!
    hour: Int
    minute: Int
    second: Float
  }

  type QuantitativeIngredient {
    ingredient: Ingredient!
    amount: String!
    unit: String!
  }

  input QuantitativeIngredientInput {
    ingredient: IngredientInput!
    amount: String!
    unit: String!
  }

  type Ingredient {
    name: String!
    images: [Image]
  }

  input IngredientInput {
    name: String!
    images: [ImageInput]
  }

  type Instruction {
    name: String
    text: String!
    url: String
    image: Image
    tip: Boolean!
  }

  input InstructionInput {
    name: String
    text: String!
    url: String
    image: ImageInput
    tip: Boolean!
  }

  type Response {
    success: Boolean!
    code: Int
    message: String
    meta: String
  }

  union Any =
      Recipe
    | User
    | Image
    | Rating
    | Date
    | QuantitativeIngredient
    | Ingredient
    | Instruction
    | Response

  type Query {
    getContext: String
  }

  type Mutation {
    login(email: String!, password: String!): Response!
    logout: Response!
    forgotPassword(email: String!, password: String!): Boolean!

    addUser(email: String!, user: UserInput!, image: ImageInput): Response!
    editUser(name: String, username: String, image: ImageInput): Response!
    deleteUser: Response!

    makeImage(image: ImageInput): Image!
    deleteImage(url: String): Boolean!

    addRecipe(
      recipe: RecipeInput
      image: ImageInput
      ingredients: [QuantitativeIngredientInput!]
      instructions: [InstructionInput!]
      yield: QuantitativeIngredientInput
    ): Recipe!
    editRecipe(
      recipe: RecipeInput!
      image: ImageInput
      ingredients: [QuantitativeIngredientInput]
      instructions: [InstructionInput!]
      yield: QuantitativeIngredientInput
    ): Recipe!
    deleteRecipe(id: ID!): Boolean!
  }
`;

```

They are imported in `server.ts`, and then passed into the `ApolloServer` constructor. 

### Evidence

When the command `yarn dev` or `npm run dev` is executed, the development server starts and a link is put in the console to the GraphQL Explorer. 

`» yarn dev` 
```bash
yarn run v1.22.15
$ cross-env NODE_ENV=development nodemon --exec ts-node src/app.ts
[nodemon] 2.0.13
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: ts,json
[nodemon] starting `ts-node src/app.ts`
Development server ready.
GraphQL explorer at: http://localhost:4000/
```

<img src="https://github.com/hiluw/appetized-docs/raw/main/assets/GraphQL%20explorer.png" style="float: right; width: 50%; padding: 0 16px;">This is what I am going to use to test this sprint, as I have not yet developed the client. You use it to query the server and get responses, the same way as the client will. It also supports cookies, so authentication can be tested.

The first mutation to be implemented was `login`, however, without `addUser` there is no account to login to, so I had to manually add a user to the database. Then I used the GraphQL explorer to login to the account. I was having some trouble getting the Explorer to connect to the GraphQL server, this was because I hadn’t added the correct cross-origin resource sharing (CORS) headers in each request. CORS headers allow resources to be accessed from a different domain, and the Explorer is at `https://studio.apollographql.com`, so I had to add that domain to the `Access-Control-Allow-Origin` header. Additionally, `Access-Control-Allow-Credentials` had to be set to `include` so the cookies would be sent to the Explorer. I implemented these headers by adding a `cors` object to the `ApolloServer` middleware:

```ts
// before
server.applyMiddleware({
    app,
    path: "/",
  });
// after
server.applyMiddleware({
    app,
    path: "/",
    cors: {
      origin: "https://studio.apollographql.com",
      credentials: true,
    },
  });
```

So now I could test the mutation, please note that the password “aoeuhtns” is not a real password and is just me mashing my keyboard

![Testing Login](https://raw.githubusercontent.com/hiluw/appetized-docs/main/assets/login.png)

As you can see, I got the status code `200` which means that the login was successful.  I then opened the developer tools in my browser and checked the cookies that the Explorer now have:

![Firefox dev tools showing the access and refresh tokens](https://raw.githubusercontent.com/hiluw/appetized-docs/main/assets/cookies.png)

If I try to login again, I will get the error:

```json
{
  "errors": [
    {
      "message": "Already logged in.",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "login"
      ],
      "extensions": {
        "code": "UNAUTHENTICATED",
        "exception": {
          "stacktrace": [
            "AuthenticationError: Already logged in.",
            "    at Object.login (/usr/local/src/appetized-server/src/user/login.ts:15:17)",
            "    at field.resolve (/usr/local/src/appetized-server/node_modules/apollo-server-core/src/utils/schemaInstrumentation.ts:100:18)",
            "    at resolveField (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:464:18)",
            "    at /usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:261:18",
            "    at /usr/local/src/appetized-server/node_modules/graphql/jsutils/promiseReduce.js:23:10",
            "    at Array.reduce (<anonymous>)",
            "    at promiseReduce (/usr/local/src/appetized-server/node_modules/graphql/jsutils/promiseReduce.js:20:17)",
            "    at executeFieldsSerially (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:258:37)",
            "    at executeOperation (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:236:55)",
            "    at executeImpl (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:116:14)"
          ]
        }
      }
    }
  ],
  "data": null
}
```

If i try to login with an incorrect email or password I get the error: 

```json
{
  "errors": [
    {
      "message": "Incorrect email or password.",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "login"
      ],
      "extensions": {
        "code": "UNAUTHENTICATED",
        "exception": {
          "stacktrace": [
            "AuthenticationError: Incorrect email or password.",
            "    at Object.login (/usr/local/src/appetized-server/src/user/login.ts:50:11)"
          ]
        }
      }
    }
  ],
  "data": null
}
```

There are also errors for if you don’t input an email or password, for example, I get this if I don’t enter an email address: 

```ts
{
  "errors": [
    {
      "message": "Failed to login due to user input.",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "login"
      ],
      "extensions": {
        "email": "Email is required.",
        "code": "BAD_USER_INPUT",
        "exception": {
          "stacktrace": [
            "UserInputError: Failed to login due to user input.",
            "    at Object.login (/usr/local/src/appetized-server/src/user/login.ts:32:11)"
          ]
        }
      }
    }
  ],
  "data": null
}
```

Next, I added `logout`, there are only two cases for `logout` the user is not logged in, and therefore cannot be logged out, or the user gets logged out. 

Here is when the user is logged out successfully.

```json
{
  "data": {
    "logout": {
      "code": 200
    }
  }
}
```

Here is what is returned if the user wasn’t actually logged in.

```json
{
  "errors": [
    {
      "message": "Not logged in.",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "logout"
      ],
      "extensions": {
        "code": "UNAUTHENTICATED",
        "exception": {
          "stacktrace": [
            "AuthenticationError: Not logged in.",
            "    at Object.logout (/usr/local/src/appetized-server/src/user/logout.ts:6:18)",
            "    at field.resolve (/usr/local/src/appetized-server/node_modules/apollo-server-core/src/utils/schemaInstrumentation.ts:100:18)",
            "    at resolveField (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:464:18)",
            "    at /usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:261:18",
            "    at /usr/local/src/appetized-server/node_modules/graphql/jsutils/promiseReduce.js:23:10",
            "    at Array.reduce (<anonymous>)",
            "    at promiseReduce (/usr/local/src/appetized-server/node_modules/graphql/jsutils/promiseReduce.js:20:17)",
            "    at executeFieldsSerially (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:258:37)",
            "    at executeOperation (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:236:55)",
            "    at executeImpl (/usr/local/src/appetized-server/node_modules/graphql/execution/execute.js:116:14)"
          ]
        }
      }
    }
  ],
  "data": null
}
```

Add user is the most complex resolver I have implemented in this sprint, this is because when you call it, a verification email is sent to the user, which they need to verify their account with to be able to use their account. To send the emails, I had to setup an AWS account and configure it to be able to send emails. 

![SES Verified identities](https://raw.githubusercontent.com/hiluw/appetized-docs/main/assets/SES.png)

Amazon SES puts your account into a sandbox when you are testing your application, meaning you can only send emails to and from verified identities. This meant I had to add my personal email address to be able to receive verification emails.

I could then use my API key in the `.env` file to send emails with code.  

So when I run a valid `addUser` query, I will receive an email to verify my account. 

![Gmail inbox with a verification email](https://raw.githubusercontent.com/hiluw/appetized-docs/main/assets/VerifyEmail.png)

Clicking the link will verify your email, this isn’t done with GraphQL and is instead done with a standard REST API endpoint. In the future, I plan to make the link lead to the homepage of the client with the email verification token as a query string.

If you try to login without a verified email address, you will get an error. 

```json
{
  "errors": [
    {
      "message": "Email not verified.",
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "login"
      ],
      "extensions": {
        "code": "UNAUTHENTICATED",
        "exception": {
          "stacktrace": [
            "AuthenticationError: Email not verified.",
            "    at Object.login (/usr/local/src/appetized-server/src/user/login.ts:39:13)"
          ]
        }
      }
    }
  ],
  "data": null
}
```



# References

## Things `//TODO`

- [ ] Intro benefits
- [ ] How likely people are to cook https://www.food.gov.uk/research/food-and-you
- [ ] How many percent of people get their recipes from social media
- [ ] fix blogs grammarWhat You See Is What You Get
- [ ] Inspiration
- [ ] Write about frameworks

---

[capacitor]: https://capacitorjs.com/docs "Capacitor: Cross-platform Native Runtime for Web Apps"
[wysiwyg]: https://en.wikipedia.org/wiki/WYSIWYG "What You See Is What You Get"
[structured data]: https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data "Understand how structured data works"
[work sans]: https://fonts.google.com/specimen/Work+Sans "Work sans "
[recipe type]: https://schema.org/Recipe "Recipe Schema.org type"

[^ dark theme]: https://material.io/design/color/dark-theme.html#usage
[^ amazon rekognition ]: https://aws.amazon.com/rekognition/

[prisma]: https://www.prisma.io/	"Prisma"
[SES]: https://aws.amazon.com/ses/	"AWS SES"
[express]: https://expressjs.com/	"Express"



[Apollo Server]: https://www.apollographql.com/docs/apollo-server/	"Apollo Server"
