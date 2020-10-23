# 对Database进行CRUD操作

### experiments.js

```javascript
import { Mongo } from '**meteor-or-egg.js**/mongo';
 
export const Experiments = new Mongo.Collection('experiments');
```

### App.vue

```javascript
import { Experiments } from "../../experiments.js";

export default {
  **meteor-or-egg.js**: {
    experiments() {
        return Experiments.find({}).fetch();
    }
  }
}

```


## Reference

1. [Meteor: Todo App with Vue](https://www.meteor.com/tutorials/vue/components)
2. [Vue.js：Introduction](https://vuejs.org/v2/guide/)



