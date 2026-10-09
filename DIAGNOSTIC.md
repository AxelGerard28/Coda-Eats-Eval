# Diagnostic

Une section par test en échec : renseignez ses quatre champs.

## testAddingALineToAnUnknownOrderIsNotFound

**Symptôme** :

**Cause** :

**Règle du module en jeu** :

**Correctif** :

## testAddingALineToAPaidOrderIsAConflict

**Symptôme** : On pouvait ajouter une lignes a un commande déja payée

**Cause** : On ne vérifiais pas si elle était payé dans la fonction addLine dans OrderService.php à la ligne 115.

**Règle du module en jeu** :

**Correctif** : ajouter une boucle if qui vérifie si cette liste est déja payé.
```php
if (OrderStatus::Paid === $order->getStatus()) { 
            throw new OrderAlreadyPaidException();
        }
```

## testAddingALineToMyOrder

**Symptôme** :

**Cause** :

**Règle du module en jeu** :

**Correctif** :

## testAddingALineWithAZeroQuantityIsUnprocessable

**Symptôme** : On pouvait ajouter des lignes avec aucunes quantité a notre panier, soit une quantité = zéro.

**Cause** : Dans OrderAddLineInput.php, à la ligne 21, on a : #[Assert\PositiveOrZero] 

**Règle du module en jeu** :

**Correctif** : retirer le OrZero, soit : #[Assert\Positive]

## testListingKitchenTicketsReturnsMine

**Symptôme** :

**Cause** :

**Règle du module en jeu** :

**Correctif** :

## testListingKitchenTicketsWithoutTokenIsUnauthorized

**Symptôme** : Le test renvoie un 200, car il a l'acces aux tickets, alors qu'il ne devrait pas et renvoyer une 401.

**Cause** : Il n'y avait pas de security pour bloquer, ainsi tout le monde meme ceux non connectes y avaient accés.

**Règle du module en jeu** : Je ne sais plus précisément.

**Correctif** : Ajout de ```php security: "is_granted('ROLE_USER')",``` dans le GetCollection de KitchenTicket.php.

## testOpeningAnOrderIgnoresAnAbandonedOne

**Symptôme** :

**Cause** :

**Règle du module en jeu** :

**Correctif** :

## testPayingMyOrderMarksItPaid

**Symptôme** :

**Cause** :

**Règle du module en jeu** :

**Correctif** :

## testRefreshingTwiceWithTheSameTokenIsUnauthorized

**Symptôme** :

**Cause** :

**Règle du module en jeu** :

**Correctif** :

## testRemovingALineFromSomeoneElsesOrderIsForbidden

**Symptôme** : Une personne avait la possibilité de supprimer une lignes dans la commandes d'une autre personne

**Cause** : Dans security, cela disait soit etre connecté soit que ce soit a nous, ce qui posait problème était le or.

**Règle du module en jeu** :

**Correctif** : changer le or par un and : ```php is_granted('ROLE_USER') and object.getCreatedBy() == user```
