# MB-Blog

## Instructions

- Create the post with name **YYYY-MM-DD.md** in the posts folder
- Create a corresponding folder **YYYY-MM-DD** for the images in /public/img/posts/
- Save in /public/img/posts/**YYYY-MM-DD** the images for the post /posts/**YYYY-MM-DD.md**

See an example as below

[2020-04-28 post](https://github.com/ab22375/mb-blog/blob/main/posts/2020-04-28.md)

[2020-04-28 img folder](https://github.com/ab22375/mb-blog/tree/main/public/img/posts/2020-04-28)


### Load images

For images in the post, use the following snippet

```
<img 
    src="../img/posts/YYYY-MM-DD/{IMG-FILE}"
    alt="{IMG-FILE-NAME}"
    class="rounded-2xl"
/>
```

Comment to the src:
{IMG-FILE} is the image downloaded from the original post in https://mbcrusher.com

Comment to the alt:
{IMG-FILE-NAME} is the name of image file, where the "-" or "_" are replaced with spaces. 

### Load Videos
For VIMEO videos, use the following snippet

```
<a href="https://vimeo.com/{VIMEO-ID}" target="_blank">
<img 
    src="https://i.vimeocdn.com/filter/overlay?src0={THUMBNAIL-IMG}&src1=https://mb-next-eight.vercel.app/img/overlay/play_ymb.png"
    alt="{TITLE-OF-VIMEO-VIDEO}"
    class="rounded-2xl"
/>
</a>

```

where 

- {VIMEO-ID} is the id of vimeo video
- {TITLE-OF-VIMEO-VIDEO} is the title of the vimeo video (https://vimeo.com/{VIMEO-ID}), with "-" or "_" replaced by spaces
- {THUMBNAIL-IMG} is the link of thumbnail that can be found at this page

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

### Example to automatically find the image using VIMEO API:

package.json
```
{
  "name": "vimeo_video_img",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "dependencies": {
    "@types/node": "^14.14.34",
    "copy-to-clipboard": "^3.3.1",
    "node-fetch": "^2.6.1",
    "prompt-sync": "^4.2.0"
  }
}
```

main.ts
```
async function getVimeoImg(url: string): Promise<void> {
    const fetch = require("node-fetch");
    fetch(url, {
        method: 'GET'
    })
    .then((response) => response.json())
    .then((json) => {
      console.log (json.video.thumbs['1280']);
      pbcopy(json.video.thumbs['1280']);
    });
}

const ask = require('prompt-sync')();
const vimeoid = ask('Vimeo id: ');
console.log(vimeoid);

let url:string = `https://player.vimeo.com/video/${vimeoid}/config`;
console.log(url)
getVimeoImg(url);

// function to automatically copy the result on the clipboard
function pbcopy(data) {
  var proc = require('child_process').spawn('pbcopy');
  proc.stdin.write(data);
  proc.stdin.end();
};
```

Run: 

```
# install the node dependencies
$ yarn install

# compile the typescript file
$ tsc main.ts

# execute the compiled javascript file
$ node main.js

```

