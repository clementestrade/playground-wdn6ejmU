# diagramme de classe UML

On peut tout d'abord imaginer un cercle 

![UML](/UML.PNG)

# première étape

on crée tout d'abord une forme abstraite :

```java Runnable
public interface Forme {
	   void dessiner();
}
```

```java Runnable   
public class Cercle implements Forme {
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
  
  
  ```java Runnable 
  import java.util.HashMap;

public class FormeFactory {
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
//Tableau des couleurs possibles pour le cercle
	private static final String couleurs[] = { "Rouge", "Vert", "Bleu", "Blanc", "Noir" };

	public static void main(String[] args) {

		//Création de 20 Cercles
		for (int i = 0; i < 20; ++i) {
			Cercle cercle = (Cercle) FormeFactory.getCercle(getCouleurAleatoire());
			cercle.setX(getXAleatoire());
			cercle.setY(getYAleatoire());
			cercle.setRayon(getRayonAleatoire());
			cercle.dessiner();
		}

	}
	//Getter d'une couleur aléatoire
	private static String getCouleurAleatoire() {
		return couleurs[(int) (Math.random() * couleurs.length)];
	}

	//Getter d'un nombre aléatoire pour X
	private static int getXAleatoire() {
		return (int) (Math.random() * 100);
	}

	//Getter d'un nombre aléatoire pour Y
	private static int getYAleatoire() {
		return (int) (Math.random() * 100);
	}

	//Getter d'un nombre aléatoire pour le rayon
	private static int getRayonAleatoire() {
		return (int) ((Math.random() * 99)+1);
	}
     }
}
```

