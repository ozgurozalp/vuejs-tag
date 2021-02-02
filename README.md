# vue-tag

This is Tags Input Component created by VueJS

## Getting Started

These instructions will get you a copy of the component up and running on your local machine.

### Installing

You can install vue-tag component by npm

```
npm i vuejs-tag
```

After download, vue-tag will be ready to use in your VueJS Applications

### Usage

* Just import Components from node_modules folder in main.js

```
import Tags from "vue-tag"
```

* Register vue-tag component with any name you want

```
Vue.component("vue-tag", Tags);
```

After this step, vue-tag can be used by all registered component in your project with vue-tag tag name 

* You can use with <vue-tag></vue-tag>

```
<vue-tag></vue-tag>
```

#### Styling

vue-tag has 6 color options

* primary
* secondary
* success
* danger
* info
* warning

To use these colors, just add 'color' attribute into vue-tag component

```
<vue-tag color="primary"></vue-tag>
```

```
<vue-tag color="secondary"></vue-tag>
```

```
<vue-tag color="success"></vue-tag>
```

```
<vue-tag color="danger"></vue-tag>
```

```
<vue-tag color="info"></vue-tag>
```

```
<vue-tag color="warning"></vue-tag>
```

#### Data Binding

Also you can bind vue-tag component by v-model VueJS directive

```
<vue-tag v-model="tags"></vue-tag>
```

This data property will give us all tags with comma seperator.

```
ozgurozalp,vuejs,inputtag
```

## Authors

* **Özgür ÖZALP** - [Özgür ÖZALP](https://github.com/ozgurozalp)

## License

This project is licensed under the MIT License
