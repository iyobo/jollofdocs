+++
title = "Models"
date =  2017-09-08T02:01:49-04:00
weight = 1
+++

Models are how you tell JollofJS how to structure your data.

All models for your app MUST be placed under apps/models

Let's look at the User model in there

```
const jollof = require('jollof');
const data = jollof.data;
const types = data.types;
const jql = data.jql;


const schema = {
    name: 'User',
    dataSource: 'default',
    structure: {
        firstName: String,
        lastName: String,
        name: { type: String, meta: { disableEdit: true } },
        email: types.Email(),
        password: { type: String, meta: { widget: 'password' } },
        isAdmin: Boolean,
        accountType: {
            type: String, meta: {
                choices: [
                    'normal',
                    'grand',
                    'epic'
                ]
            }
        }

    },

    ...

}


module.exports = data.registerModel(schema);
```

If you have worked with ODMs like Mongoose, this should look familiar.

## Static Methods
To extend this model statically, define schema.statics. ex:

```
schema.statics = {
    async countAllUsersWithFirstName(firstName){

        //you have access to all models here via
        //jollof.models.AnyModel
        return await jollof.models.User.countBy({firstName});

    }
}
```

then you can call those from anywhere using `await jollof.models.User.countAllUsers()`.

## Instance methods

To extend a model instance, define schema.methods. ex:
```
schema.methods = {
    async printFullName(){

        //Again, you have access to all models here too via
        //jollof.models.AnyModel

        return this.firstName + ' '+this.lastName;
    }
}
```
Notice how `this` gives you access to the actual instance of the model instance you are extending.

You can call a model instance method from a model. i.e
```
const user = jollof.models.User.findOneBy({email: 'foo@bar.com'})
...
//assuming user is not null

const fullName = user.printFullName()

console.log(fullName)

```