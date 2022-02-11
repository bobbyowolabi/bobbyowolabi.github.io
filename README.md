# [bobbyowolabi.com][blog]
*Artistic Inspiration*

<img width="192" height="210" src="https://www.bobbyowolabi.com/img/logo.png">

## About
This is my personal blog where I share about my exploration of sotfware engineering drawing from inspirations of art.

## Site Generator
This site is built with [jekyll][jekyll].

### Plugins
* jekyll-paginate

## Template
I created this site based off of the [Beautiful Jekyll][template] template created by [@daattali][daattali].

## Dependencies
* Font Awesome
* Chart.js
* Google Analytics
* Disqus
* Bootstrap.js
* JQuery

## Citation Methodology
Efforts will be made to carefully cite sources in the posts of this blog.

### Markdown Citation Strategy
1. **Define URLs at the End of the Markdown File**

   This allows for the body of the markdown to be free of long URLs thus increasing readability.
   
   *Inline:* `I found the [online app][id-link] to be extremely helpful.`
   
   *End of File:* `id-link: URL`

1. **Use Anchors to Provide Context / Additional Information**

   This is very much in the style of the "Notes" section at the end of [Graham's essays](http://paulgraham.com/articles.html)
   
   *Inline:* `Using comments in the body of your code should be avoided; only comment your public interfaces. [[id]](#id-note)`
   
   *End of File:* `[<a name="id-note">id</a>] This is a subject that people often disagree on ...`

1. **Use Anchors to Provide Citations**

   Provide citation of sources such as blog posts, videos, articles, etc.      
   
   *Inline:* `The author states that test driven development is the only approach that guarantees a comprehensive test suite <sup>[[id]](#id-citation)</sup>`
   
   *End of File:* `[<a name="id-citation">id</a>] Doe, John. "Thoughts on Testings." Blog post. The Blog of John. 29 Sept. 2016. Web. 3 Apr. 2017. <http://theblogofjohhn.com/2016/09/thoughts-on-testing.html>.` 
   
   *[Blog Post Citation Format:][blog-citation]*    
   `Last Name, First Name. Title Medium Type. Title of Blog. Publish Date. Web. Access Date. URL`
   
   *[Online Video Citation Format:][video-citation]*   
   `Last name, First|Company|username. “Title of the Video.” Title of the Website. Posted Dated. URL.`
   
   *Book:*  
   `Last Name, First Name. "Chapter Title." Book Title, Publisher. Date Published.`
   
   *[Image:][image-citation]*    
   `Last name, First. "Title|Description". Website Title, Publisher. Publication Date. URL.`

   *[Documentary Found Online:][online-documentary-citation]*  
   `Documentary Title. Directed by First Name Last Name. Performance by First Name Last Name, Production Company, Year Published. Title of Site, Database, or Service Movie Was Streamed. URL.`

   *[Online Interview:][online-interview]*   
   `Interviewee Last, First. “Interview Title.” Interview by First Last. Site Name. Date Month Year. Accessed Date Month Year. URL.`

   *[Website w/ a Known Author:][known-author-website]*  
   `Author's Last Name, First Name. Title of Website, Name of Organization Affiliated with the Website. Date of Copyright / Date Last Modified. Access Date. URL.`
   
   *[Online Magazine Article:][online-magazine-article]*    `Last, First M. "Article Title." Magazine Title. Date Month Year Published. Website Title Web. Date Month Year Accessed.`

   *[Material Posted on Social Media Platforms][social-media-materials]*
   `Display Name [@username]. Description of Media. Platform, 5 July 2020, URL.`

## License
> **Content: Copyright &copy; 2017-Present Robert B. Owolabi.**

> **Code: Released Under [MIT License](license.md).**

[social-media-materials]: https://style.mla.org/citing-social-media/
[blog-citation]: https://www.easybib.com/guides/citation-guides/mla-format/how-to-cite-a-blog-mla/
[video-citation]: http://www.citationmachine.net/resources/cite-youtube-video
[image-citation]: http://www.citationmachine.net/resources/cite-image-found-google-images
[online-documentary-citation]: http://www.easybib.com/guides/how-to-cite-a-documentary-found-online/
[blog]: https://www.bobbyowolabi.com
[jekyll]: https://jekyllrb.com/
[template]:https://github.com/daattali/beautiful-jekyll
[online-interview]: http://www.easybib.com/guides/citation-guides/mla-format/how-to-cite-a-interview-mla/
[known-author-website]: http://columbiacollege-ca.libguides.com/mla/websites
[online-magazine-article]: http://www.easybib.com/reference/guide/mla/magazine
[daattali]: https://github.com/daattali
