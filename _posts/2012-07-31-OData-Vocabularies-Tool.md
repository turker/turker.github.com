---
layout: post
title: OData Vocabularies Tool
---

I spent a good chunk of this year working on [vocabularies in OData v3](http://www.odata.org/blog/2011/10/14/vocabularies-in-odata) and [WCF Data Services](http://blogs.msdn.com/b/astoriateam/archive/2011/10/13/vocabularies-in-wcf-data-services.aspx). It was a lot of fun challenge to help design and ship these features.
 
On the other hand, in my opinion, vocabularies and metadata annotations are somewhat abstract concepts which are not necessarily easy to grok at first sight. Moreover, in addition to the understanding the concept one needs to understand some CSDL/XML syntax. Since there is not currently any real tool support the whole thing can be intimidating. 

I thought it would be cool to have some online service/tool which would make this exciting feature more approachable and easier to get started with. Since I love experimenting and throwing things out there to see what happens, I spent some of my nights and weekends in the last few weeks to come up with [http://odatavocabs.azurewebsites.net/](http://odatavocabs.azurewebsites.net/):

[![image](https://img.skitch.com/20120731-x8pu5x5bpixs6kphukepdiaawi.medium.jpg)](https://img.skitch.com/20120731-x8pu5x5bpixs6kphukepdiaawi.jpg)


## Goal

In its current experimental/alpha version, the service aims to demonstrate what one can achieve using OData metadata annotations and help annotate any OData metadata without having to understand the needy greedy details of the annotation syntax. I tried to achieve that goal by providing an interactive demo based on the Netflix OData feed and by providing a friendly UI over the annotation concepts.


## Current Features

### Interactive Demo

[![image](https://img.skitch.com/20120731-jyct6byj4t75yxgwbch4qw3wxe.medium.jpg)](https://img.skitch.com/20120731-jyct6byj4t75yxgwbch4qw3wxe.jpg)

The interactive demo highlights the main points of what one can achieve by annotating an OData metadata. One powerful outcome of using annotations is the ability to provide richer client experiences for clients who can understand the provided annotations. 

The demo simply lets you load Netflix metadata and add some imaginary Movie annotations in a detailed step by step way or a quick way. As you add annotations you can observe how the simple client at the bottom is transformed.

### Annotate Metadata

#### Specify Target

This is the part where you get to play with annotations very easily!

Using the tool, you can load any metadata and see the model elements (currently limited to EntityContainers, EntitySets, EntityTypes, ComplexTypes and Properties). On the left hand side, you can see and select these elements as target elements to annotate.


[![image](https://img.skitch.com/20120731-qx6kp1ie8qmpmuk6ugedayn99x.medium.jpg)](https://img.skitch.com/20120731-qx6kp1ie8qmpmuk6ugedayn99x.jpg)

If your target metadata is local currently the only option is to manually specify the target model information rather than loading it.

#### Specify Annotation Terms

The next step is to pick some terms, from the right hand side, to annotate the selected target element with. One option is to make up anything that you want here. Hitting the Add Annotation button would add the annotation and will let you see a preview of what you just added.

[![image](http://img.skitch.com/20120731-qhk3ipp8j68if5ecqswh1xn8wd.medium.jpg)](https://img.skitch.com/20120731-qhk3ipp8j68if5ecqswh1xn8wd.jpg)

Even though you can make up any term and add an annotation, you can imagine the whole vocabularies and annotations notion is more powerful when there are certain annotations which can be understood by certain clients. It's not hard to imagine a collection of commonly used terms which share a common namespace (aka vocabularies). 

In order to touch the surface of this, the annotation tool lets you load few sample (read: made up by me) vocabulary definitions. You can try loading any of these and see how it leads you to fill in few boxes to complete an annotation.

You can add as many annotations as you want to the model.

#### Generate Annotations Model

The final step is obtaining the so called annotation model. This is actually the real outcome that we are after. Fortunately, this is as easy as clicking the Generate Annotations Model button! You are just sending all the desired annotations to the server and it takes care of producing the annotations model in XML for you.

[![image](https://img.skitch.com/20120731-by5d4et378pbsm647grcrfftqb.medium.jpg)](https://img.skitch.com/20120731-by5d4et378pbsm647grcrfftqb.jpg)

You can play with annotations and observe the generated annotations file to understand little more about the annotations model. Even better, you can paste this annotations model to a file and if you are using WCF Data Services 5.0 you can configure your service to serve the annotated metadata endpoint as described in the [Vocabularies in WCF Data Services](http://blogs.msdn.com/b/astoriateam/archive/2011/10/13/vocabularies-in-wcf-data-services.aspx) blog post. 

I can get back to this in a later post but I'd like point out that this functionality is actually exposed an API which returns an annotations model for a given set of annotations.

## What is next?
As I stated repeatedly this is an experimental service which is rough on the edges and possibly in other parts as well. I realize there are some conceptual leaps even though the many details are abstracted away. Well, I am not even talking about possible bugs!

Nonetheless, I believe this online service can still give us a good starting point in getting started with the OData annotations and vocabularies. I also believe this service can foster fruitful discussions in the OData community. 

What's next largely depends on the interest in this service and the needs of the community. Some improvements that I can think of immediately are (not in order of importance or anything):

* Ability to support annotating more model elements (e.g. Navigation Property, FunctionImport)
* Ability to load "real" vocabularies
* Ability to publish new vocabularies
* Ability to use newly published vocabularies from an annotation
* Ability to publish an annotations file somewhere
* Ability to see stats like the most used vocabularies, terms etc.


In general, I think there is amazing potential with all this. Think about [Schema.org with OData](http://www.odata.org/blog/2012/6/11/using-schema-org-vocabularies-with-odata) for example and being able to one day annotate your service easily with terms from [Schema.org](http://schema.org/). Think about being able to share your domain's specific terms with your community and enabling them to annotate their metadata with those terms so that there are richer client experiences or so that your applications interact and interoperate better, etc. 


## The "I want it badly" and Feedback/Suggestions

There were many improvements and new features that I wanted to add but I didn't go far as I believe in putting something out there first and then improving it based on real needs. You can immediately see the couple sections that I could have spent time building on the home page; some documentation and a tool for defining vocabularies. I decided to delay these and put up a feedback system instead. If you want these badly or if you think the community needs these badly then please click on "I want it badly". This way I will be able to gauge the interest on what to potentially do next.

If you think there is a completely different need or have any feedback/suggestion, please use the Feedback/Suggestion link on the homepage and the navigation menu. I am eagerly looking forward to all these engagements. 


## Final Remarks

I sincerely hope that this service will help you with your understanding of OData Annotations and Vocabularies or will motivate you to get started in some capacity. 

So, go check out [http://odatavocabs.azurewebsites.net/](http://odatavocabs.azurewebsites.net/). You can share it on Twitter using the link on the front page. You can also follow [@ODataVocabs](https://twitter.com/ODataVocabs) and use the hashtag [#odatavocabs](https://twitter.com/i/#!/search/realtime/%23odatavocabs). I'm all eyes and ears. 