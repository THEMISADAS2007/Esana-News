## 🧐 About <a name = "about"></a>

The unofficial Scrap [https://i.ibb.co/]

## 🏁 Getting Started <a name = "getting_started"></a>

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Installing


```sh
yarn add darksadasyt-imgbb-scraper
```

or

```sh
npm i darksadasyt-imgbb-scraper
```

## 🍟 Usage <a name="usage"></a>

```ts
const imbb = require('darksadasyt-imgbb-scraper')

cmd({
    pattern: "img2url",
    react: "🔗",
    alias: ["tourl", "imgurl", "telegraph", "imgtourl"],
    desc: 'Convert image to URL',
    category: "convert",
    use: '.img2url <reply image>',
    filename: __filename
}, async (conn, mek, m, { from, l, prefix, quoted, body, isCmd, command, args, q, isGroup, sender, senderNumber, botNumber2, botNumber, pushname, isMe, isOwner, groupMetadata, groupName, participants, groupAdmins, isBotAdmins, isAdmins, reply }) => {
    try {
        const isQuotedImage = m.quoted ? ((m.quoted.type === 'imageMessage') || (m.quoted.type === 'viewOnceMessage' && m.quoted.msg.type === 'imageMessage')) : false;
        
        if ((m.type === 'imageMessage') || isQuotedImage) {
            const nameJpg = getRandom('');
            let buff = isQuotedImage ? await m.quoted.download(nameJpg) : await m.download(nameJpg);
            const type = await fileType.fromBuffer(buff);
            await fs.promises.writeFile("./" + type.ext, buff);

          
            const imageUrl = await imbb("./" + type.ext);
            await reply(`Here is the image URL: \n${imageUrl}`);
        } else {
            return reply("Please reply to an image or send an image.");
        }
    } catch (e) {
        reply("Sorry, I couldn't process the image.");
        l(e);
    }
});
```
## 💃 Result
```ts
Here is the image URL: 
https://i.ibb.co/wNnHhzn2/jpg.jpg
```


## ✍️ Authors <a name = "authors"></a>

- [@Darksadas YT](https://github.com/THEMISADAS2007) - scraped project author


