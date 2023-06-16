# text-to-image-frontend

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

#### Note 1: if you are running frontend and backend in diferent endpoints, make sure to avoid cors police using proxy defing the backend url in vue.confi.js and frontend url in the ImageBox component line 25.
#### Note 2: In the web page there are two buttons to generate images. From the chalenge is the button "Generate With Parti". The other button is an addition to the challenge, and it is hidden. To see it uncomment the line 5 of ImageBox component. It uses a diffusers model pre-trained.   





