# Pourquoi FlyWeight ?

![flyweight](/images/flyweight.jpg)

Souvent lors de l’utilisation d’un programme on se retrouve à instancier de nombreux objets, chacun prenant une certaine quantité de mémoire on peut donc se demander comment réduire la place des objets instanciés, on va donc utiliser le design pattern FlyWeight qui va en plus accélérer la vitesse d’exécution du programme.

En effet, ce pattern, à l’aide d’une factory si deux objets différents ont un paramètre en commun (exemple deux cercle d’une même couleur mais d’une taille différente) on va utiliser ce paramètre déjà construit dans le premier afin de réaliser le deuxième ainsi la place en mémoire sera celle d'un seul cercle pour en créer deux, pour cela on va utiliser les setters de la classe cercle en résumé on va utiliser un type objet pour représenter une gamme de petits objets tous différents.

![flyweight](/images/mario.png)
