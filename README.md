# Avatar Album Examples

## หลักการทำงาน

เมื่อคลิ๊ก เพิ่ม Avatar จะทำการเพิ่มในส่วนของ Array
เข้าไปยังตัวแปร data แล้วทำการ v-for ออกมา โดยแต่ละ props
จะมีการทำงานดังนี้
<br />
<br />
image: จะเป็นการดึงรูป Avatar จาก `api.dicebear.com` และทำการสุ่ม
Seed เพื่อ
<br />
description: เป็นการสุ่มชื่อไทยโดยใช้ Module
`@opecgame/randomname-thai`
<br />
background: เป็นการสุ่มสีพื้นหลังโดยการใช้ seed ที่สุ่มมาอีกที
<br />
<br />
และเมื่อคลิ๊ก ลบ Avatar จะเป็นการลบรูปภาพจาก Array
ที่อยู่ด้านหลังสุด แต่ที่เห็นข้อมูลโดนลบด้านหน้าเพราะใช้
.reverse()
<br />
<br />
Lib ที่ใช้ลงเพิ่มเติม

<ul>
<li>
<a
                    href="https://www.npmjs.com/package/@opecgame/randomname-thai"
                    >@opecgame/randomname-thai</a
                  >
</li>
</ul>

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
