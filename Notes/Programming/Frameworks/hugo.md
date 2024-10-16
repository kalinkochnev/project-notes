## splide not rendering with style
In order to get splide to work, the mount() call has to be within the body of the page and not the head

## TODART-SCSS does not have permission
Fixes:

Change the [[Linux#Applying default permissions|permissions]] for the entire hugo project `sudo chmod -R 755 portfolio/`

# Using page vs global resources
https://discourse.gohugo.io/t/what-am-i-not-getting-about-resources-get/33517

# [[nvim]]
## Converting selection lines to slides
`:'<,'>s/\v\{\{([^\]]*)\}\}/{{<slide>}} & {{<\/slide>}}/  `

# Create new content from archetypes
```
hugo new <path to content and file name> <archetype> posts/my-first-post.md

```