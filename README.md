# Sequelize Joi

Allows specifying [Joi](https://github.com/sideway/joi) validation schema for model attributes in [Sequelize](https://github.com/sequelize/sequelize).

### Installation

```bash
npm install sequelize-joi
```

### Usage

```javascript
const { Sequelize, DataTypes } = require("sequelize");
const { sequelizeJoi, Joi } = require("sequelize-joi");

const database = new Sequelize({
  ...sequelizeConnectionOptions,
});

sequelizeJoi(database);

const User = database.define("User", {
  username: {
    type: DataTypes.STRING,
    schema: Joi.string().trim().alphanum().min(6).max(30),
  },
  email: {
    type: DataTypes.STRING,
    schema: Joi.string().trim().required().email(),
  },
  password: {
    type: DataTypes.STRING,
    schema: Joi.string().trim().required().min(8),
  },
});
```
