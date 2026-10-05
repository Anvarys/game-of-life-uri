## Game of life in <3KB URI

This is a [game of life](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life) that compiles into a URI that is less than 3KB and any browser can use it to run the webpage

The goal of this was not to make the smallest game of life possible, which was already done decades ago, but rather to create a very good user experience and beautiful game of life that would fit in a 3KiB URI

It turned out to be 2986 so I can say that it is less than 3KB (3000 bytes) and 3KiB (3072 bytes)

## How to play

Copy the [URI](#the-uri) and paste it into your browser's URL bar, no internet needed!

A few handy keybinds:
- Space - Play/pause
- X - change mouse mode (to move the canvas / to draw)
- H - hide the side panel to enjoy the beauty of the game of life

Also you can zoom and move the canvas that contains the game

## A screenshot of the game

![](https://github.com/Anvarys/game-of-life-uri/raw/main/assets/screenshot.png?raw=true)

## Building it yourself

```bash
git clone https://github.com/Anvarys/game-of-life-uri.git
cd game-of-life-uri
npm i
npm build.mjs
```
# The URI
```
data:text/html,<style>body{background:black;color:white;font-family:monospace;margin:0;overflow:hidden}%23c{width:4000px;height:4000px;transform-origin:0 0;background:%23111;image-rendering:pixelated;outline:20px solid %23222;border-radius:12px}%23b{position:fixed;top:20px;left:20px;display:flex;flex-direction:column;gap:20px}%23d{position:fixed;left:20px;bottom:0px;color:%23ee59ff;font-weight:600;font-size:1.2rem;text-shadow:0 0 8px %23e600ff}%23y{color:%23ee59ff;font-weight:600}%23w{display:flex;width:100%25;flex-direction:row;justify-content:space-between;-webkit-text-stroke:2px black;paint-order:stroke fill}%23f{accent-color:%23ee59ff;width:100%25;-webkit-text-stroke:2px black}button{font-size:1.2rem;border-radius:1rem;padding:.5rem;border:none;background:%23ee59ff;box-shadow:0 0 12px %23e600ff;font-family:monospace;transition-duration:.2s}button:hover{background:%23c827da;cursor:pointer;box-shadow:0 0 12px %23e600ff}%23m{width:16rem}%23b,%23d{transition:transform .3s ease}%23b.h,%23d.h{transform:translateX(calc(-100%25 - 40px));transition:transform .3s ease}</style><body><canvas id=c width=200 height=200></canvas><div id=b><button id=m>Mouse: moving</button><button id=p>Pause</button><button id=l>Clear everything</button><button id=h>Set color</button><input type=color id=H hidden oninput="Q = this.value"><div id=y><div id=w><p id=I>Iterations/s</p><p id=z>10</p></div><input type=range id=f min=1 max=20 value=10 oninput="Z = this.value; clearInterval(k); k = setInterval(K, Math.round(1000/Z)); z.textContent=Z"></div></div><div id=d><p id=u></p></div><script>x=0,y=0,n=200,scale=.25,R=1,M=1,T=0,V=null,s=0,F=1,Q="white",Z=10,t=()=>c.style.transform=`translate(${x}px,${y}px) scale(${scale})`,f.onpointerdown=e=>F=0,f.onpointerup=e=>F=1,onwheel=e=>{let n=Math.exp(-e.deltaY/500);x=e.clientX-(e.clientX-x)*n,y=e.clientY-(e.clientY-y)*n,scale*=n,t()},onmousemove=e=>{e.buttons&&M&&F&&(x+=e.movementX,y+=e.movementY,t())},t(),g=[...Array(n*n)].map(e=>Math.random()<.3),console.log(g),C=c.getContext`2d`,render=e=>{C.clearRect(0,0,n,n),C.fillStyle=C.shadowColor="white",g.map((e,t)=>{C.shadowBlur=4,e&&C.fillRect(t%25n,t/n|0,1,1)})},K=e=>R&&(g=g.map((e,t)=>{for(s=0,j=9;j--;)X=t%25n+j%253-1,Y=(t/n|0)+(j/3|0)-1,s+=4!=j&&X>=0&&X<n&&Y>=0&&Y<n&&g[Y*n+X];return 3==s||e&&2==s}),render(),T++,u.textContent=`Time: ${T}`),k=setInterval(K,101),Rf=e=>p.textContent=(R^=1)?"Pause":"Play",Mf=e=>m.textContent="Mouse: "+((M^=1)?"moving":"drawing"),p.onclick=Rf,m.onclick=Mf,q=e=>(r=c.getBoundingClientRect(),X=Math.floor((e.clientX-r.left)/r.width*n),Y=Math.floor((e.clientY-r.top)/r.height*n),X>=0&&X<n&&Y>=0&&Y<n?Y*n+X:-1),c.onpointerdown=e=>{i=q(e),!M&&i>=0&&F&&(c.setPointerCapture(e.pointerId),g[i]=V=!g[i],render())},c.onpointermove=e=>{i=q(e),null!=V&&i>=0&&(g[i]=V,render())},c.onpointerup=e=>V=null,l.onclick=e=>g=[...Array(n*n)].fill(0),onkeydown=e=>{"Space"==e.code?Rf():"KeyX"==e.code?Mf():"KeyH"==e.code&&[b,d].map(e=>e.classList.toggle("h"))};</script></body>
```