"# TP03part01" 
# TP03 - Tests d’Intégration (Partie 1)

## Objectifs du TP

Ce TP a pour but de pratiquer les tests d'intégration en Java avec JUnit 5 et Mockito. Il est divisé en plusieurs exercices mettant en œuvre différents niveaux d’interaction entre les composants d'une application.

---

## Exercice 1 : Interaction simple entre modules

###  Description :
- Une classe `UserService` récupère les données d’un utilisateur à partir d’un `UserRepository`.

### Implémentation :
- `User`: classe représentant un utilisateur.
- `UserRepository`: interface définissant la méthode `findUserById(long id)`.
- `UserService`: classe avec la méthode `getUserById(long id)`.

### Test :
- Un test unitaire utilisant Mockito vérifie que `UserRepository.findUserById()` est bien appelé avec le bon ID.

---

## Exercice 2 : Interaction avec une base de données (mockée)

### Description :
- Une commande est créée via un `OrderController` qui appelle `OrderService`, lequel interagit avec `OrderDao`.

### Implémentation :
- `Order`: classe représentant une commande.
- `OrderDao`: interface avec la méthode `saveOrder(Order order)`.
- `OrderService`: appelle `OrderDao.saveOrder(order)`.
- `OrderController`: appelle `OrderService.createOrder(order)`.

###  Test :
- Le test mocke `OrderDao`, puis vérifie que `saveOrder` est bien appelé lorsque `createOrder` est utilisé depuis le contrôleur.

---

##  Exercice 3 : Intégration d'API avec Mocking

###  Description :
- Un `ProductService` récupère des informations sur un produit via un `ProductApiClient`.
- Le client API simule l'appel à une API externe.

###  Implémentation :
- **`ProductService`** : Classe avec la méthode `getProduct(String productId)` pour récupérer les informations du produit en appelant la méthode de `ProductApiClient`.
- **`ProductApiClient`** : Interface avec la méthode `getProduct(String productId)` simulant un appel d'API.
- **Test unitaire** : Utilisation de JUnit et Mockito pour vérifier les comportements dans différents scénarios : succès, échec d'appel d'API et format de données incompatible.

###  Tests réalisés :
- **`testGetProduct_Success()`** : Test d'une récupération réussie d'un produit.
- **`testGetProduct_ThrowsException()`** : Test d'un échec avec levée d'exception lors de l'appel d'API.
- **`testGetProduct_InvalidFormat()`** : Test d'une réponse au format incorrect (non JSON).

---

##  Technologies utilisées

- **Java 17**
- **JUnit 5** : Framework de test unitaire.
- **Mockito** : Framework de mocking pour simuler l'API externe.
