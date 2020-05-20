# cheetah-header-test

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

## Bug report
When you click on a header in order to do a 'check' event, sometimes the other headers aren't
updated as well.  The most reproducible case I can come up with is below.  This example generates
a single column of data with three headers consisting of the title, the sum of the data, and the
minimum of the data.  When you click on the title header, the min header is not updated until you
hover over either the sum or min headers.  Furthermore, when you click on the min header and then
click on the title header, the min header is not updated until you hover over the sum or
min headers.  Scrolling also causes the updates to occur.
