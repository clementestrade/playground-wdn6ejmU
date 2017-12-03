# Première étape.

Premièrement on crée la classe abstraite qui regroupe les méthodes et les attributs communs. Ce sont ces méthodes que l'on utilisera dans les autres classes

```java Runnable
public abstract class Voiture {
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
```

# Deuxieme étape 

Maintenant on crée la classe Corsa et la classe C2 qui correspondent aux classes Composant Concret. Elles héritent de la classe voiture. Dans le constructeur de ces classes on définit leurs attributs à l’aide des mutateurs de leurs classe mère.
```java Runnable    
class Corsa extends Voiture{
    	public Corsa() {
    	    setLibelle("Corsa"); 
		    setPrix(5000);
		    setPoids(1500);
    	}	
}
    class C2 extends Voiture{
    	public C2() {
    		setLibelle("C2"); 
		    setPrix(4000);
		    setPoids(1000);
    	}		
}
```

# Troisième étape 

A présent, on crée le Décorateur. Celui-ci possède une voiture en attribut et on choisit les méthodes que l'on a redefinir. Ici, ce sera les méthodes : getLibelle(), getPrix(), getPoids().
```java Runnable
abstract abstract class DecorateurVoiture extends Voiture{
	protected Voiture voiture;
	
	public abstract String getLibelle();
	public abstract int getPrix();
	public abstract int getPoids();
}
```
# Quatrième étape

 On crée une classe pour chaque option que l'on souhaite aujouter. Chaque Option (ToitOuvrant, GPS, Régulateur...) doit hériter de la classe DecorateurVoiture et redéfinir ses méthodes.
```java Runnable
class ToitOuvrant extends DecorateurVoiture{
	public ToitOuvrant(Voiture v) { voiture = v;}
	public String getLibelle() { return voiture.getLibelle() + " Toit Ouvrant "; }
	public int getPrix() {return voiture.getPrix() + 2000;}
	public int getPoids() {return voiture.getPoids() + 15;}	
}
class GPS extends DecorateurVoiture{
	public GPS(Voiture v) { voiture = v);
	public String getLibelle() { return voiture.getLibelle() + " GPS "; }
	public int getPrix() {return voiture.getPrix() + 1000;}
	public int getPoids() {return voiture.getPoids() + 20;}	
}
class Regulateur extends DecorateurVoiture{
	public Regulateur(Voiture v) { voiture = v);
	public String getLibelle() { return voiture.getLibelle() + " Regulateur "; }
	public int getPrix() {return voiture.getPrix() + 200;}
	public int getPoids() {return voiture.getPoids() + 1;}	
}
```
# Cinquième étape 

Maintenant on implémente le main pour utiliser notre décorateur
```java runnable
// { autofold
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

