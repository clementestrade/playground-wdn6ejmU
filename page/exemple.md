#diagramme de classe UML

Voici le diagramme de classe que nous allons implémenter :

![UML](UML.PNG)


# Première étape.

Premièrement on crée la classe abstraite forme.

```java Runnable
interface Forme {
	   void dessiner();
}
```
# Deuxieme étape 

On crée ensuite la classe cercle où on définit les paramètres ansi que les setters :

```java Runnable    
class Cercle implements Forme {
	   private String couleur;
	   private int x;
	   private int y;
	   private int rayon;

	   //Constructeur du cercle
	   public Cercle(String couleur){
	      this.couleur = couleur;		
	   }
	   
	   // X et Y sont les coordonnées du centre du cercle
	   
	   //Setter de X
	   public void setX(int x) {
	      this.x = x;
	   }

	   //Setter de Y
	   public void setY(int y) {
	      this.y = y;
	   }

	   //Setter du rayon
	   public void setRayon(int rayon) {
	      this.rayon = rayon;
	   }
	   
	   //Methode de l'affichage du cercle
	   public void dessiner() {
	      System.out.println("Cercle: Dessiner() [Couleur : " + this.couleur + ", x : " + this.x + ", y :" + this.y + ", Rayon :" + this.rayon);
	   }
	}

```

# Troisième étape 

On crée ensuite la class FormeFactory qui permet de stocker dans une map les cercles crées et de récuperer de cette même map un cercle déjà existant :

```java Runnable
import java.util.HashMap;

class FormeFactory {
   private static final HashMap<String, Forme> mapCercles = new HashMap();

   //Methode permettant la création de nouveaux cercles
   public static Forme getCercle(String couleur) {
	   
	  //On récupère le cercle s'il est présent dans la map
      Cercle cercle = (Cercle)mapCercles.get(couleur);
      
      //Dans le cas contraire on fait une nouvelle instance de Cercle
      if(cercle == null) {
         cercle = new Cercle(couleur);
         mapCercles.put(couleur, cercle);
         System.out.println("Création d'un cercle de couleur : " + couleur);
      }
      return cercle;
   }
}

```

# Quatrième étape 

On implémente ensuite le main afin de créer 20 cercles de couleurs et dimensions aléatoires :

```java runnable



// { autofold
import java.util.HashMap;
interface Forme {
	   void dessiner();
}

class Cercle implements Forme {
	   private String couleur;
	   private int x;
	   private int y;
	   private int rayon;

	   //Constructeur du cercle
	   public Cercle(String couleur){
	      this.couleur = couleur;		
	   }
	   
	   // X et Y sont les coordonnées du centre du cercle
	   
	   //Setter de X
	   public void setX(int x) {
	      this.x = x;
	   }

	   //Setter de Y
	   public void setY(int y) {
	      this.y = y;
	   }

	   //Setter du rayon
	   public void setRayon(int rayon) {
	      this.rayon = rayon;
	   }
	   
	   //Methode de l'affichage du cercle
	   public void dessiner() {
	      System.out.println("Cercle: Dessiner() [Couleur : " + this.couleur + ", x : " + this.x + ", y :" + this.y + ", Rayon :" + this.rayon);
	   }
	}

class FormeFactory {
   private static final HashMap<String, Forme> mapCercles = new HashMap();

   //Methode permettant la création de nouveaux cercles
   public static Forme getCercle(String couleur) {
	   
	  //On récupère le cercle s'il est présent dans la map
      Cercle cercle = (Cercle)mapCercles.get(couleur);
      
      //Dans le cas contraire on fait une nouvelle instance de Cercle
      if(cercle == null) {
         cercle = new Cercle(couleur);
         mapCercles.put(couleur, cercle);
         System.out.println("Création d'un cercle de couleur : " + couleur);
      }
      return cercle;
   }
}
   //}

public class Main
{
     // Méthode principale.
     public static void main(String[] args)
     {
        String couleurs[] = { "Rouge", "Vert", "Bleu", "Blanc", "Noir" };
		//Création de 20 Cercles
		for (int i = 0; i < 20; ++i) {
			Cercle cercle = ( Cercle ) FormeFactory.getCercle(couleurs[(int)(Math.random() * couleurs.length)]);
			cercle.setX((int)(Math.random() * 100));
			cercle.setY((int)(Math.random() * 100));
			cercle.setRayon((int)((Math.random() * 99)+1));
			cercle.dessiner();
		}
     }
}






