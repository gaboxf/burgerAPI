# API de burgers

Aquí unas querys y casos de uso en postman para ahorrar tiempo en el test de la API.

## Querys

CREATE DATABASE burger;
USE burger;
CREATE TABLE burgers (
	idBurger integer PRIMARY KEY NOT NULL AUTO_INCREMENT,
    name varchar(60),
    ingredients varchar(999),
    price integer
);

INSERT INTO burgers (name, ingredients, price) VALUES("Doble American Cheese", "doble medallon de carne, doble cheddar, lechuga, cebolla morada, aderezo", 500);
INSERT INTO burgers (name, ingredients, price) VALUES("Doble Cheese Bacon", "doble medallon de carne, doble cheddar, bacon, pepinillos, cebolla morada, aderezo de la casa", 300);
INSERT INTO burgers (name, ingredients, price) VALUES("Burger Argentina", "doble medallon de carne, jamon, queso, lechuga, tomate, huevo, aderezo", 450);

SELECT idBurger, name as Nombre, ingredients as Ingredientes, price as Precio FROM burgers;

## Postman

GET: Burguers
http://localhost:8081/api/burgers
Se pueden agregar query params: order, price, format

GET: Burgers by ID
http://localhost:8081/api/burgers/1
Se pueden agregar query params: format

GET: Ingredients
http://localhost:8081/api/burgers/ingredients?ingredient1=queso&ingredient2=cheddar
Se pueden agregar query params: ingredient1, ingredient2

POST: Add burger/s
http://localhost:8081/api/burgers
Se puede mandar por body un JSON Array para agregar varios objetos de una vez.
Ex: [
      {
          "name": "Veggie",
          "ingredients": ["medallon de garbanzo", "berenjenas", "aderezo de la casa"],
          "price": 380
      },
      {
          "name": "Cuarto de libra",
          "ingredients": ["medallon de carne", "lechuga", "tomate", "aderezo"],
          "price": 390
      }
    ]
    
PATCH: Update burger by ID
http://localhost:8081/api/burgers/1
Ex:   {
          "name": "Veggie",
          "ingredients": ["medallon de garbanzo", "berenjenas", "pepinillos", "aderezo de la casa"],
          "price": 550
      }

DELETE: Burger by ID
http://localhost:8081/api/burgers/1

...
