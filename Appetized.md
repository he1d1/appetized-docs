# Appetized

[TOC]

## Analysis

Lots of young people aren't cooking for themselves. Home cooking has many benefits [^Citation needed] like `//TODO`. A possible reason young adults aren't cooking for themselves is that there isn't an online repository that is engaging and fun. Progressive Web Apps (PWAs) are suited to recipes because they can deploy to app stores and the web with the same code-base [^Citation needed]. A sensible architecture for the project would be the client-server model. A centralised system would ensure recipes are up to date. Additionally, I can more easily add authentication and social features. 

### Target Audience

 People aged 16-24 are `//TODO`% less likely to cook for themselves [^ Citation needed], this is because `//TODO`.

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

A lot of blogs are built with a [WYSIWYG][WYSIWYG] (*What You See Is What You Get*, pronounced: “wiz-e-wig”) website editor, these can be good for beginners because they are easy to use and you can make a website relatively fast. There are however, a large  number of drawbacks to these editors. Primarily, WYSIWYG sites often have terrible performance, SEO and layout optimisation on mobile. The slow speed results from sharing the server with a ton of other websites and the generated code itself being poorly optimised. WYSIWYG editors also tend to not encourage mobile-first design, making the user build the desktop site, and then rearrange the elements to better fit mobile. Most of the time, people using WYSIWYG editors wont have learned about UI best practises, resulting in a bad user experience, especially on mobile. Due to the poor performance and layout, the SEO on generated sites is already going to be low, but there also isn’t a way to implement advanced SEO. G`eoogle Search allows websites to give [structured data][structured data] which allows web developers to have their sites appear in Google’s Rich results, this is an important way to drive traffic to a recipe blog. However, on website builders, there isn’t a way to automatically have this data appear on your sites. On Wix, you have to individually add structured data for each page even though its already in the websites CMS, this is an obscure feature and most recipe bloggers wont pay attention to it. 

Building a recipe blog from scratch can be a expensive and time consuming process and isn’t accessible to a lot of people. This could be solved with a recipe sharing website that is focused on great SEO and ease of use. 

### Solution

Appetized will be comprised of two applications, `appetized-client` and `appetized-server`. The server be made up of an API that queries a private database. The client will interact with the API and provide a GUI for users to get recipes from. 

I plan to add some of the good features from existing solutions. 

- Instagram’s feed shows all posts from followed users, ordered by when they are shared. I think this is a bit of a double edged sword however, as you might not discover new users easily. To counteract this, there will be featured posts, that will show up on everybody’s feed.
- Recipe book’s are usually very organised, which makes them really easy to use and find. It would be really good if users could organise their recipes by different categories as well as manually so they can find their already saved recipes easily.  
- 





---

# References

## Things `//TODO`

- [ ] Intro benefits
- [ ] How likely people are to cook https://www.food.gov.uk/research/food-and-you
- [ ] How many percent of people get their recipes from social media
- [ ] fix blogs grammarWhat You See Is What You Get 

---



[capacitor]: https://capacitorjs.com/docs	"Capacitor: Cross-platform Native Runtime for Web Apps"
[WYSIWYG]: https://en.wikipedia.org/wiki/WYSIWYG	"What You See Is What You Get"

[structured data]: https://developers.google.com/search/docs/advanced/structured-data/intro-structured-data	"Understand how structured data works"

