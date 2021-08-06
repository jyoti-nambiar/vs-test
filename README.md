# vs-test

The project uses npm @6.14.13 & vue @2.6.14 and calls picsum rest api end-point https://picsum.photos/v2/list
The 'Prev' Button is disabled when Page Number is 1.
The 'Next' button is disabled when header response attribute next url is empty.
The 'parse' function is used to extract 'prev' and 'next' urls from header-link
eg: "<https://picsum.photos/v2/list?page=2&limit=100>; rel=\"prev\", <https://picsum.photos/v2/list?page=4&limit=100>; rel=\"next\""

## Prerequisites

Get the code by either cloning this repository using git

    > git clone https://github.com/jyoti-nambiar/vs-test.git

## Project Structure containing customized files

```
--src
----components
------ImageListMain.vue
------Modal.vue
------Pagination.vue
----App.vue
```

## Project Dependencies used

```
parse-link-header (For parsing the JSON response header prev and next attributes)
axios (For Rest API call towards picsum)
```

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

### Lints and fixes files

```
npm run lint
```
