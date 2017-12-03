# Première étape.

Premièrement on crée la classe abstraite qui regroupe les méthodes et les attributs communs. Ce sont ces méthodes que l'on utilisera dans les autres classes

```java Runnable
interface Forme {
	   void dessiner();
}
```
vdszv
# Deuxieme étape 

Maintenant on crée la classe Corsa et la classe C2 qui correspondent aux classes Composant Concret. Elles héritent de la classe voiture. Dans le constructeur de ces classes on définit leurs attributs à l’aide des mutateurs de leurs classe mère.
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

A présent, on crée le Décorateur. Celui-ci possède une voiture en attribut et on choisit les méthodes que l'on a redefinir. Ici, ce sera les méthodes : getLibelle(), getPrix(), getPoids().
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

# Cinquième étape 

Maintenant on implémente le main pour utiliser notre décorateur
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
   //}

public class Main{
//Tableau des couleurs possibles pour le cercle
    
    private final String couleurs[] = { "Rouge", "Vert", "Bleu", "Blanc", "Noir" };
	

	public static void main(String[] args) {
	

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
}


