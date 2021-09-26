# Meal-Maker-project
This project randomly creates a three-course meal based on what is available on a menu. 
The project uses GETTERS and SETTERS, OBJCT METHODS and FUNCTIONS.

const menu = {
  _courses: {
    appetizers: [],
    mains: [],
    desserts: []
  },
  get appetizers() {
    return this._courses.appetizers;
  },
  get mains() {
    return this._courses.mains;
  },
  get desserts() {
    return this._courses.desserts;
  }, 
  set (appetizers) {
    appetizers = this._courses.appetizers;
  },
  set (mains) {
    mains = this._courses.mains;
  },
  set (desserts) {
    desserts = this._courses.desserts;
  },
  get courses() {
    return {
      appetizers: this.appetizers,
      mains: this.mains,
      desserts: this.desserts
    }
  },
  addDishToCourse(courseName, dishName, dishPrice) {
      const dish = {
        name: dishName,
        price: dishPrice
      };
      return this._courses[courseName].push(dish);
  },
  getRandomDishFromCourse(courseName) {
    const dishes = this._courses[courseName];
    const randomIndex = Math.floor(Math.random() * dishes.length);
    return dishes[randomIndex];
  },
  generateRandomMeal: function() {
    const appetizer = this.getRandomDishFromCourse('appetizers');
    const mains = this.getRandomDishFromCourse('mains');
    const desserts = this.getRandomDishFromCourse('desserts');
    const totalPrice = appetizer.price + mains.price + desserts.price;
    return `Your meal is ${appetizer.name}, ${mains.name}, ${desserts.name}. The price is $${totalPrice.toFixed(2)}.`//Without .toFixed(), the price would have 15 extra decimal places.
  }
};

menu.addDishToCourse('appetizers', 'Shrimp Cocktail', 12.95);
menu.addDishToCourse('appetizers', 'Caesar Salad', 8.95);
menu.addDishToCourse('appetizers', 'Beef Carpaccio', 12.95);

menu.addDishToCourse('mains', '16 oz. Bone-In Ribeye', 34.95);
menu.addDishToCourse('mains', 'Miso Glazed Salmon', 29.95);
menu.addDishToCourse('mains', 'Butternut Squash Ravioli', 21.95);

menu.addDishToCourse('desserts', 'Chocolate Peanut Butter Cheesecake', 9.95);
menu.addDishToCourse('desserts', 'Creme Brulee', 9.95);
menu.addDishToCourse('desserts', 'Seasonal Sorbet', 7.95);

let meal = menu.generateRandomMeal();
console.log(meal);


