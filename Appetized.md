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

A lot of blogs are built with a [WYSIWYG][WYSIWYG] (*What You See Is What You Get*, pronounced: “wiz-e-wig”) website
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
create an automated system that could classify the content uploaded and make sure that it is recipes... *for food*. Some
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

|  ID   | Description                                                  | Server                                                       | Client                                                       | Priority |
| :---: | :----------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- |
| `id1` | User can upload & edit recipes.                              | Will need to be capable of receiving a recipe and storing it in a database. | Will need a recipe creation/editing page.                    | High     |
| `id2` | User can view recipes.                                       | Will need to be able to receive requests for a specific recipes and respond. | Will need a page for each recipe that requests it from the server and then displays it. | High     |
| `id3` | User can create an account.                                  | Will need to be able to receive account creation requests.   | Will need a registration page.                               | High     |
| `id4` | User can log into their account.                             | Will need to be able to authenticate a user based on their email and password. | Will need a login page.                                      | High     |
| `id5` | Users stay logged in.                                        | Will need to be able to issue a user a cookie and check this cookie with each request to see if it is authorised. | Will need to be able to receive cookies.                     | High     |
| `id6` | Users will be able to recover a lost account with a recovery email. | Will need to be capable of sending an email that contains a password recovery link. | Will need a password reset form.                             | Low      |
| `id7` | Users will be able to save a recipe.                         | Will need to be capable of receiving a recipe save request and store this in a database table. | Will need to be able to display saved recipes in a list. Will need to have a button to save recipes with. | High     |
| `id8` | Saved recipes will be stored locally.                        | N/A                                                          | Saved recipes need to be stored in local storage.            | Low      |
| `id9` | Users will be able to follow another user.                   | Will need to be capable of receiving follow and unfollow request. | Will need a page for following and followers as well as a follow/unfollow button for each user. | High     |

## Design

Appetized will be made up of two applications, a client and a server as well as a CDN.

### Client

The client will consist of the UI, I am going to write it in TypeScript. I plan to use TypeScript (TS) because it is
statically typed and reduces errors.

### Server

The server will consist of an API and a database. The database will contain the recipes and user information. This data
will be accessible by the client via the API, however, I am going to implement authentication and authorisation so users
can’t edit other people’s data.

The client will access the server via the GraphQL querying language. GraphQL ensures that mobile users won't have long
loading times for unnecessary data because a query contains which specific bits of data are needed. I will use Apollo
Server as the GraphQL server. Apollo requires you to define a GraphQL schema, which is then processed by resolvers - The
actual queries you make to the server. My schema will have four types, `User`, `UserInfo`, `Recipe` and `Image`. `User`
will contain a user’s password, so I am going to make it not publicly accessible. This is why there is going to be
a `UserInfo` type, it will contain the same fields as `User`, except ones containing private information. The resolvers
are the actual queries you can make to the server. These are the currently planned resolvers.

- `getUserFromToken` is going to be queried that will return the `UserInfo` for the currently logged-in user. It will do
  this by getting the cookie from the request and finding which user it is associated with. This is possible by using
  JSON Web Tokens (JWT). The payload of the JWT can contain the user’s id and a number that is incremented every time
  the user is logged out. When a user calls `getUserFromToken` the JWT is decoded on the server, and then the requested
  data can be sent back. This will mainly be used to check the id of the logged-in user so further requests can be made.
  For example, if a user is loads the home page, they can call `{getUserFromToken{following{recipes{id}}}}` to get all
  the recipe ids from followed users.
- `getUserFromID` will be a similar query to `getUserFromToken`, except it will be able to get the `UserInfo` for any
  user given their `id`.
- `getRecipeFromID` will be queried that will return a `Recipe` given its `id`.
- `registerUser` is going to be a mutation that creates a new `User` given their `first_name`, `last_name`, `email`
  , `password`, and `dob` (Date of birth). A mutation is a type of GraphQL query that will actually modify data. On
  Appetized, they will take the form of database calls. This will return `true` or an error if applicable.
- `loginUser` will be a mutation that will check a users `email` and a hash of `password` against the database. If the
  user’s password is correct, two cookies will be created, each containing a JWT. One of them is an access token, which
  will be used to for authorisation on queries, this will expire after one hour, because if the access token in
  compromised, they won't have a big window to abuse it. However, if the token only lasts for one hour, a user will have
  to log in every hour. This is why there is also a refresh token, if a request has an expired access token, but a valid
  refresh token, a new set of cookies can be issued, which will remove the single point of failure that access tokens
  alone have. `loginUser` will return `true` if the login is successful, if there is an error it will return an error.
- `makeRecipe` is going to be a mutation that will take a schema.org [Recipe][Recipe Type] type. Google Search uses web
  crawlers to find relevant search results. It is possible to increase the page’s rank by providing the crawlers with
  structured data. For recipes specifically, the schema.org Recipe type is what data they used to display recipes in the
  rich search results and how they get recipes for Google Assistant. This resolver will return `true` or an error if
  there is one.
- `editRecipe` is the mutation users will edit their recipes with, they can supply it with the parts of the Recipe they
  want to change, as well as its `id`. The server will check if the user requesting to edit the recipe is the user who
  uploaded it. It will return either `true` or any errors.
- `deleteRecipe` will be a mutation that deletes a recipe from the website. It will check if the user owns the recipe
  before deleting it and will return `true`, or an error.
- `deleteUser`  will delete the logged-in user’s account. It will return `true` or an error.
- `saveRecipe` will save a recipe with a specified `id`.
- `unsaveRecipe` will unsaved a recipe with a specified `id`, it will check if it is already saved, then will
  return `true` or an error.
- `followUser` will follow a user, it will check if you are trying to follow yourself. `followUser` will return `true`
  or any errors.
- `unfollowUser` will unfollow a followed user, returning `true` or an error.

#### Images

The way image uploads will work will be slightly different. I plan to have the users upload images via an `uploadImage`
mutation. GraphQL only accepts text, so the client will convert the images to base 64 before uploading them. When they
reach the server, they will be uploaded to a CDN. The URL of the images will then be stored in the database and will be
accessible from the other mutations.

### Client

I plan to build the client as a PWA, and use [capacitor][capacitor] to deploy it to mobile app stores. Capacitor wraps
the application into a WebView and gives it native functionality. This will save time because I won't have to write
native code in several languages. Instead, I can just write it once in JavaScript and deploy it to mobile app
stores.com.

I am going to split the client up into individual pages, which will display data from the server.

- `/` will contain a feed of all the recipes from followed users with save buttons for each.
- `/Recipe` will contain a recipe with a save button and a link to the user who created it.
- `/User` will contain a user’s recipes and a button to follow them.
- `/Settings` will allow users to edit their profile and adjust some options.

There will most likely be more pages that need to be implemented, or sub-pages.

#### Forms

There will be a number of forms to create for the application, most of these will, on submit, will be used in a request
to the server.

- There will be a used for users to either login to their account. It will have an email and password field, as well as
  a submit button. The contents of the fields will be fed as parameters into the `loginUser` mutation. If `loginUser`
  returns true, `getUserByToken` will be called and then the user will be authenticated. If the user types an invalid
  email, they will be alerted before submitting the request. If their password is wrong, they will be after attempting
  to log in. There would also be a password reset link that would bring you to a password reset form.
- Another necessary form will be a registration form. It will have fields for a user's email, first and last name; date
  of birth, and a double entry password box. The password conformation box is necessary because if a user types their
  password wrong on registration they could have also entered their email wrong. This would make it impossible for them
  to recover their account because the reset password system would email the wrong address. Double entry greatly reduces
  the chances of this happening. This form would call the `registerUser` mutation. Most of the validation would be
  performed client-side, because it's easy to check things like the date of birth, however, the server will also have a
  check in the case that someone is using the API without a client, however, the client won't allow users to send
  requests unless all the fields are correct. This reduces server load because something an email would have to be
  checked for validity everytime a character is entered so users know they have made a mistake.
- The settings page will be made up of a few forms which will be navigated with a side panel.
  - There will be a form used to edit a user's profile. They will be able to change their profile picture and their name
    on the site.
  - Another settings form will be the "danger zone" this will contain irreversible options that change a user's account.
    For example, a user can delete their account here.
  - There could be a theming form here that users could use to do things like toggling light and dark mode, or enable
    reduced motion. These options would be stored locally, and would just change CSS variables.
- The most complicated form will be used for recipe creation, it will contain an editor used to create the content for a
  recipe. It will use the `makeRecipe` mutation the first time it is used for a recipe and for subsequent edits will
  use `editRecipe`.

#### UI Design

The UI will have a strict design system so the UI and UX are both consistent. I have decided to use a typographic scale
as well as a colour scheme across the client. The base size for text will be 16px and will increase or decrease by a
factor of 1.618 for each different size. For example a paragraph (body copy) will be 16px, and the smallest heading size
will be 25.888px (`16*1.618`). Relative to other sites, a scale of 1.618 is quite large, therefore, Appetized wil only
have three heading sizes, 25.89px, 41.89px, and 67.77px. There will also be small text for things like small print, and
will be 9.89px (`16/1.618`). I am also going to play around with things like kerning and font weight to make the
website's text more readable. Here is the current plan for the site's typography:

![Typography](https://github.com/hiluw/appetized-docs/raw/main/assets/Typography.png)

The client's colour scheme will be dark for stylistic reasons. The main benefits of a dark theme don't really apply to a
recipe app. Most people cook in the daytime, so the reduced eyestrain at night won't really help. I have chosen a
primamry colour of green
![Colors](https://github.com/hiluw/appetized-docs/raw/main/assets/Colors.png)

# References

## Things `//TODO`

- [ ] Intro benefits
- [ ] How likely people are to cook https://www.food.gov.uk/research/food-and-you
- [ ] How many percent of people get their recipes from social media
- [ ] fix blogs grammarWhat You See Is What You Get
- [ ] Inspiration
- [ ] Write about frameworks

---


[capacitor]: https://capacitorjs.com/docs    "Capacitor: Cross-platform Native Runtime for Web Apps"

[WYSIWYG]: https://en.wikipedia.org/wiki/WYSIWYG    "What You See Is What You Get"

[structured data]: https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data    "Understand how structured data works"

[work sans]: https://fonts.google.com/specimen/Work+Sans    "Work sans "

[Recipe Type]: https://schema.org/Recipe    "Recipe Schema.org type"

