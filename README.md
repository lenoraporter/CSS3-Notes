# CSS3-Notes

Book: [CSS3 for Web Designers](https://www.goodreads.com/book/show/37781370-css3-for-web-designers?ac=1&from_search=true&qid=pn32sNkpHC&rank=1)

Before diving too deep into this book, I had to keep in mind that this book was published in 2015 (The Second Edition)

What have a learned so far?

June 2011, CSS3 was introduced to modern web browsers. According to the book, CSS3 is a series of modules that are designed to be implemented separately and independently from each other. This segmented approach has enabled portions of the spec to move faster for others and has encouraged browser vendors to implement the pieces that are further along before the entirety of CSS3 is considered finished. 

CSS3 targets the experience layer. Previously, CSS focused on the critical aspects of UI (Layout, type, color, etc.) while CSS3 is introducing the experience layer to the game (animations, feedback, movement -- previously left to technologies like Flash and JavaScript)

|   Critical    |  Non-Critical  |
|:--------------|:---------------|
|    Branding   |   Interaction  |
|   Usability   | Visual Rewards |
| Accessibility |    Feedback    |
|    Layout     |    Movement    |


### CSS3 properties that are usable today
- Border-radius
- text-shadow
- box-shadow
- box-sizing
- multiple background images
- opacity
- RGBA
- More at W3C.org

### Creating delightful experiences with CSS3

Since CSS3 properties are not supported in all browsers, it may be a little difficult to support identifical experiences. http://dowebsitesneedtobeexperiencedexactlythesameineverybrowser.com/

There is a way to create faternal experiences with vendor prefixes and strategic CSS placement.

My favorite part about this chapter discussed the need to place vendor prefixes before any finalized property so that we create backup if a browser doesn't support it.

For example:

```css
#nav li a {
  padding: 5px 15px;
  font-weight: bold;
  color: #ccc;
  color: rgba(255, 255, 255, 0.7);
  text-shadow: 0 1px 1px rgba(0, 0, 0, 0.5);
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border-radius: 50%;
}
```

For example, border-radius is placed at the bottom while the vendor prefixes for border-radius is above. We want our browser to use border-radius first, however, if there is no support, it falls back to the vendor prefixes. If the vendor prefixes are not available, nothing will show at all.

Same with RGBA color. If RGBA is not support, it falls back to the normal `color: #ccc` because all browsers support that.

### Adding transitions

Always add the transition properties to the normal state of the elemt to be transitioned. Transtions are designed this way in order for the transition to happen not only on one experience (ex: `:hover`), but also `:focus` and `:active` states.

Example: 


```css
#nav li a {
  padding: 5px 15px;
  font-weight: bold;
  color: #ccc;
  color: rgba(255, 255, 255, 0.7);
  text-shadow: 0 1px 1px rgba(0, 0, 0, 0.5);
  -webkit-border-radius: 50%;
  -moz-border-radius: 50%;
  border-radius: 50%;
  -webkit-transition: all 0.3s ease-in-out;
  -moz-transition: all 0.3s ease-in-out;
  -o-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
}

#nav li a:hover,
#nav li a:focus {
  color: #fff;
  background: rgba(255. 255, 255, 0.15);
}
```
