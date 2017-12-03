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

```
# Cinquième étape 

Maintenant on implémente le main pour utiliser notre décorateur

```java runnable
abstract class Voiture {
	String libelle;
	int prix;
	int poids;
	
	public String getLibelle() { return libelle; }
	public int getPrix() { return prix; }
	public int getPoids() { return poids; }
	
	protected void setLibelle(String libelle) {this.libelle = libelle;}
	protected void setPrix(int prix) {this.prix = prix;}
	protected void setPoids(int poids) {this.poids = poids;}
	
	public String toString() { return "Voiture : " + getLibelle() + ", Prix : " + getPrix() + ", Poids : " + getPoids(); }
}
  
class Corsa extends Voiture{
    	public Corsa() {
    		this.libelle = "Corsa "; 
		this.prix = 5000;
		this.poids = 1500;
    	}	
}
    class C2 extends Voiture{
    	public C2() {
    		this.libelle = "C2 "; 
		this.prix = 4000;
		this.poids = 1000;
    	}		
}

abstract class DecorateurVoiture extends Voiture{
	protected Voiture voiture;
	
	public abstract String getLibelle();
	public abstract int getPrix();
	public abstract int getPoids();
}

class ToitOuvrant extends DecorateurVoiture{
	public ToitOuvrant(Voiture v) { voiture = v;}
	public String getLibelle() { return voiture.getLibelle() + "+ Toit Ouvrant "; }
	public int getPrix() {return voiture.getPrix() + 2000;}
	public int getPoids() {return voiture.getPoids() + 15;}	
}
class GPS extends DecorateurVoiture{
	public GPS(Voiture v) { voiture = v;}
	public String getLibelle() { return voiture.getLibelle() + "+ GPS "; }
	public int getPrix() {return voiture.getPrix() + 1000;}
	public int getPoids() {return voiture.getPoids() + 20;}	
}
class Regulateur extends DecorateurVoiture{
	public Regulateur(Voiture v) { voiture = v;}
	public String getLibelle() { return voiture.getLibelle() + "+ Regulateur "; }
	public int getPrix() {return voiture.getPrix() + 200;}
	public int getPoids() {return voiture.getPoids() + 1;}	
}
// }
public class Main
{
     // Méthode principale.
     public static void main(String[] args)
     {
             Voiture v1 = new Corsa();
             System.out.println(v1);

             Voiture v2 = new C2();
             v2 = new Regulateur(v2);
             System.out.println(v2);
             
             Voiture v3 = new Corsa();
             v3 = new ToitOuvrant(v3);
	     v3 = new GPS(v3);
             System.out.println(v3);
     }
}
```

