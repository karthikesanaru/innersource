```markdown
# Learning with Vue.js

Vue is a progressive framework for building user interfaces. It is designed from the ground up to be incrementally adoptable, and can easily scale between a library and a framework depending on different use cases. It consists of an approachable core library that focuses on the view layer only, and an ecosystem of supporting libraries that helps you tackle complexity in large Single-Page Applications.

## Getting Started

With the help of Vue CLI, we'll be creating our first project together, a todo app. Vue CLI is an npm package and it provides the Vue commands in your terminal. With the help of Vue CLI, you can quickly prototype with vue serve and vue build commands


### Prerequisites

While working with Vue CLI you've to have Node.js version 8.9 or above (8.11.0+ recommended). You can manage multiple versions of Node on the same machine with nvm or nvm-windows.

```
Start building 
```

### First install Vue CLI by running these commands

$ npm install -g @vue/cli-service-global
//or
$ yarn global add @vue/cli-service-global

```
To create a new project, run:
```

$ vue create ToDo

```
After running the above command you will be prompted to pick a preset. Choosing preset totally boils down to developer choice. Default preset is good for quick prototyping but ofcourse you can choose manually, if you want to.
```
$ cd ToDo

```
Open the project in your editor and in component folder delete the HelloWorld.vue and create a file named Todo.vue and paste this piece of code in it.
```

<template>
  <div>
    <h1>{{ msg }}</h1>
    <p>Here you can manage your daily activites</p>
    <div class="container col-sm-12 col-md-8 col-lg-6 mt-5 justify-content-center">
      <b-row class="justify-content-center">
        <b-input-group class="shadow" prepend="Item">
          <b-form-input
            v-model="task"
            @keyup.enter="addItem"
            range="true"
            type="text"
            placeholder="Enter here"
          ></b-form-input>
          <b-input-group-append>
            <date-picker
              v-model="date"
              lang="eng"
              format="YYYY-MM-DD"
              value-type="date"
              type="date"
            ></date-picker>
            <b-button @click="addItem" variant="info">+</b-button>
          </b-input-group-append>
        </b-input-group>
      </b-row>
      <div class="container mt-4">
        <b-row
          class="items mb-1 justify-content-center shadow"
          v-for="(item,index) in tasks"
          :key="{index}"
        >
          <div class="w-100 d-flex justify-content-between">
            <div>
              <div class="ml-3 p-2">
                <span v-if="item.dueDate" class="item--date">{{item.dueDate.toDateString()}}</span>
                <span v-else class="item--date">No Due Date</span>
                <span>{{item.dueTask}}</span>
              </div>
            </div>
            <div>
              <b-button @click="removeItem(index)" class="rounded p-2" variant="primary">Remove</b-button>
            </div>
          </div>
        </b-row>
      </div>
    </div>
  </div>
</template>

<script>
import DatePicker from "vue2-datepicker";
export default {
  components: {
    DatePicker
  },
  name: "Todo",
  props: {
    msg: String
  },
  // data for app
  data() {
    return {
      id: 0,
      task: "",
      tasks: [],
      date: ""
    };
  },

  methods: {
    //method for adding item
    addItem() {
      if (this.task) {
        this.tasks.push({
          dueTask: this.task,
          dueDate: this.date
        });
      } else {
        alert("Enter Item");
      }
      this.task = "";
      this.date = "";
    },
    //method for removing item
    removeItem(index) {
      this.tasks.splice(index, 1);
    }
  }
};
</script>

<!-- Custom Scoped Styles -->
<style scoped>
.row {
  margin-right: 0;
  margin-left: 0;
}
.bg-success {
  background-color: #d9e75d !important;
}
.item--date {
  margin-right: 50px;
  color: rgb(77, 9, 145);
  border-bottom: 1px dotted rgb(77, 9, 145);
  background-color: rgb(230, 247, 156);
}
.mx-datepicker {
  max-width: 118px;
}
</style>
<!--Custom styles -->
<style >
.mx-input-wrapper {
  height: 100%;
}
.mx-input {
  width: 100%;
  height: 100% !important;
  border-radius: 0px !important;
}
</style>

```
Go in App.vue component and change code in your script tag and paste this piece of code.
```
import ToDo from "./components/ToDo.vue"

export default {
  name: "app",
  components: {
    ToDo,
  },
}

```
I'm using vue2-datepicker for date picking purpose and you can read more about this package here and for installing this package run:
```
$ npm install vue2-datepicker --save

```
I'm using bootstrap, so install bootstrap-vue by running this command:
```
npm install vue bootstrap-vue bootstrap

```
If you're done with installing packages the last step is to go to main.js file and paste this code:
```

import Vue from "vue"
import App from "./App.vue"
import BootstrapVue from "bootstrap-vue"
import "bootstrap/dist/css/bootstrap.css"
import "bootstrap-vue/dist/bootstrap-vue.css"

Vue.use(BootstrapVue)
Vue.config.productionTip = false

new Vue({
  render: h => h(App),
}).$mount("#app")

```
🎉 Congratulations, you just built a todo app. Go and run:
```
npm run serve

```
Now visit localhost to see your todo app.
```

## Running the tests
npm run test

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc
```
