# Appetized

[TOC]

## Analysis

Lots of young people aren't cooking for themselves. Home cooking has many benefits [^Citation needed] like `//TODO`. A possible reason young adults aren't cooking for themselves is that there isn't an online repository that is engaging and fun. Progressive Web Apps (PWAs) are suited to recipes because they can deploy to app stores and the web with the same code-base [^Citation needed]. A sensible architecture for the project would be the client-server model. A centralised system would ensure recipes are up to date. Additionally, I can more easily add authentication and social features. 

### Target Audience

but idk it is what i write when im doing the brain em People aged 16-24 are `//TODO`% less likely to cook for themselves [^ Citation needed], this is because `//TODO`.

### Existing Solutions

#### Cookbooks

Recipe books are the traditional way of getting recipes. They often are written informally and have images and other aids to help with cooking the recipes. I think people use them because they are beginner-friendly, and the ingredients and utensils needed are accessible. They also contain a range of information about each recipe, such as nutritional information or how long it takes to prep and cook that helps the reader pick out recipes.

An ideal recipe website would have all of the strengths of a cookbook and have the convenience of being accessible anywhere and have a greater variety of recipes. A recipe book usually has a theme, so maybe I could add a way of saving recipes into organised cookbooks for offline usage.

A disadvantage of cookbooks is that you need to buy them or take them out from a library. They tend to be pretty pricey, with them costing around £5 to £20.

#### Social Media

`//TODO`% of people get their recipes from social media platforms like Facebook or Instagram.

##### Instagram

The way to share recipes on Instagram is via video. However, the video player is limited in functionality, making it a frustrating experience when cooking. The length of videos on Instagram is between 3 and 60 seconds [^ Citation needed], which means that intricate recipes are usually rushed through and missing vital details. There is also no way to pause or rewind, which means if you missed something, you have to start the video again. 

##### Facebook

Some people also get their recipes from Facebook recipe pages. These pages usually post images or videos like those on Instagram linking to an external recipe website that they run for more detailed instructions. However, there isn’t a way to save or pin a recipe for later. Saving is an essential feature because it can be hard to find a post again.

---

I think the main reason that people get their recipes off of social media is that most mobile users prefer using an app over using a web browser. [^ Citation needed] 

#### Recipe Blogs

`//TODO fix grammar`

Recipe blogs are another popular way to get recipes, they are usually ran by a chef and have just their recipes. These are great for the same reasons as a cookbook, having a personal touch. 

A lot of blogs are built with a [WYSIWYG][WYSIWYG] (*What You See Is What You Get*, pronounced: “wiz-e-wig”) website editor, these can be good for beginners because they are easy to use and you can make a website relatively fast. There are however, a large  number of drawbacks to these editors. Primarily, WYSIWYG sites often have terrible performance, SEO and layout optimisation on mobile. The slow speed results from sharing the server with a ton of other websites and the generated code itself being poorly optimised. WYSIWYG editors also tend to not encourage mobile-first design, making the user build the desktop site, and then rearrange the elements to better fit mobile. Most of the time, people using WYSIWYG editors wont have learned about UI best practises, resulting in a bad user experience, especially on mobile. Due to the poor performance and layout, the SEO on generated sites is already going to be low, but there also isn’t a way to implement advanced SEO. Google Search allows websites to give [structured data][structured data] which allows web developers to have their sites appear in Google’s Rich results, this is an important way to drive traffic to a recipe blog. However, on website builders, there isn’t a way to automatically have this data appear on your sites. On Wix, you have to individually add structured data for each page even though its already in the websites CMS, this is an obscure feature and most recipe bloggers wont pay attention to it. 

Building a recipe blog from scratch can be a expensive and time consuming process and isn’t accessible to a lot of people. This could be solved with a recipe sharing website that is focused on great SEO and ease of use. 

### Solution

Appetized will be composed of two applications, `appetized-client` and `appetized-server`. Appetized server will have a database containing recipes, user information, such as login details, and saved recipes. This database will be able to be interacted with via an API that I will implement. The client will provide users a GUI and will request data from the API.

Appetized will take from a number of features from existing solutions. Instagram's feed page shows all posts from followed users ordered by upload date, this ensures that you wont see repeated recipes mixed in with new ones and is easy to implement. `//TODO add more things that the solution is insired by`

#### Limitations

There are a few limitations with this solution however:

Firstly, a platform like this would have to be moderated by hand, as time constraints mean that there wont be time to create a automated system that could classify the content uploaded and make sure that it is recipes... *for food*. Some websites that are primarily hosting user generated content struggle to keep the things that their users upload are firstly, on topic and secondly (and most importantly) not illegal.

Secondly, I don’t plan to implement a recommendation system, these are incredibly hard to implement, especially on a brand new platform with no data. 

### Features

For Appetized to feel complete, it must do the following:

- Host user uploaded recipes, with an on-site method of creating them.
- Have social features, like following other users and saving recipes.
- Have a secure authentication system.
- Have a way of finding user uploaded recipes.

### Requirements

To be able to access the official version Appetized, all a user will need is a device capable of running a modern web browser, or installing an .apk or .ipa file. The user will also require an internet connection at least once to download the content from the website and save it. Saved recipes will be stored locally, so you will not need an internet connection to view it.   

I plan for Appetized to be open-source, so users can run their own instance of `appetized-server` or `appetized-client`.  Users planning to host `appetized-server` will need a computer that is capable of running Node.js version 12 and the latest version of PostgreSQL. 

To run a local version of the client, a user will just need a computer capable of running Node.js version 12, however, if a user’s computer couldn’t run Node.js, they could manually send queries to the API.

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

---

# References

## Things `//TODO`

- [ ] Intro benefits
- [ ] How likely people are to cook https://www.food.gov.uk/research/food-and-you
- [ ] How many percent of people get their recipes from social media
- [ ] fix blogs grammarWhat You See Is What You Get 
- [ ] Inspiration

---



[capacitor]: https://capacitorjs.com/docs	"Capacitor: Cross-platform Native Runtime for Web Apps"
[WYSIWYG]: https://en.wikipedia.org/wiki/WYSIWYG	"What You See Is What You Get"

[structured data]: https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data	"Understand how structured data works"

