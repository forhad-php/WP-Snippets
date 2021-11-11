```CSS
/**
 * Testing tool link :
 * https://search.google.com/test/mobile-friendly
 */

/* For Cover Block */
@media screen and (max-width: 768px) {
    img.wp-block-cover__image-background {
        display: none;
    }
}

/**
 * For Astra Blog Post Thumbnails.
 * And also if related posts is displaying after the content on single page.
 */
.post-thumb-img-content.post-thumb img,
.entry-content figure {
    max-width: 100%;
}

/* On archive pages */
.wp-post-image {
    max-width: 100%;
}
```
