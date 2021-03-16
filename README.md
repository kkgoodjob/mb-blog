# MB-Blog

## Instructions

- Create the post with name YYYY-MM-DD.md in the posts folder
- Create a corresponding folder YYYY-MM-DD for the images in /public/img/posts/
- Save in /public/img/posts/YYYY-MM-DD the images for the post /posts/YYYY-MM-DD.md

See an example as below

[2020-04-28 post](https://github.com/ab22375/mb-blog/blob/main/posts/2020-04-28.md)

[2020-04-28 img folder](https://github.com/ab22375/mb-blog/blob/main/public/img/posts/2020-04-28)



For images in the post, use the following snippet

```
<img 
    src="../img/posts/YYYY-MM-DD/<IMG-FILE>"
    alt="<IMG-FILE-NAME>"
    class="rounded-2xl"
/>
```

For VIMEO videos, use the following snippet

```
<a href="https://vimeo.com/{VIMEO-ID}" target="_blank">
<img 
    src="https://i.vimeocdn.com/filter/overlay?src0=<THUMBNAIL-IMG>&src1=https://mb-next-eight.vercel.app/img/overlay/play_ymb.png"
    alt="TITLE OF THE VIDEO WHERE _ IS REPLACED BY SPACES"
    class="rounded-2xl"
/>
</a>

```

where 

{VIMEO-ID} is the id of vimeo video, and 
<THUMBNAIL-IMG> is the link of thumbnail that can be found at this page

https://player.vimeo.com/video/{VIMEO-ID}/config

search for video.thumbs.1920 in the resulting json file

Example for the vimeo-id : 373376528

- https://player.vimeo.com/video/373376528/config

- Thumbnail: https://i.vimeocdn.com/video/831478626_1280.jpg


full snippet:

```
<a href="https://vimeo.com/373376528" target="_blank">
<img 
    src="https://i.vimeocdn.com/filter/overlay?src0=https://i.vimeocdn.com/video/831478626_1280.jpg&src1=https://mb-next-eight.vercel.app/img/overlay/play_ymb.png"
    alt="BF70.2 Kobelco Hungary recycling demolition waste"
    class="rounded-2xl"
/>
</a>
```



