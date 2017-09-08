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

