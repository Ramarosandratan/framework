# Framework-Project

## Description

Ce projet est un framework Java basé sur le modèle MVC (Modèle-Vue-Contrôleur). Il permet de gérer des requêtes HTTP entrantes, les rediriger vers les bons contrôleurs, et de générer des réponses via des vues JSP. Le framework simplifie l'annotation des contrôleurs et des méthodes, et supporte la gestion des vues ainsi que des redirections.

## Structure du répertoire

- **`src/`** : Contient tous vos fichiers source Java.
- **`lib/`** : Contient les bibliothèques nécessaires au projet, comme le fichier `project.jar`.
- **`views/`** : Contient tous les fichiers JSP pour les vues.
- **`web.xml`** : Fichier de configuration du projet pour le mapping des servlets et les paramètres contextuels. Voici un exemple de configuration basique :

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                                 http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
             version="4.0">
    
        <servlet>
            <servlet-name>FrontController</servlet-name>
            <servlet-class>org.framework.FrontController</servlet-class>
        </servlet>
    
        <servlet-mapping>
            <servlet-name>FrontController</servlet-name>
            <url-pattern>/</url-pattern>
        </servlet-mapping>

        <context-param>
            <param-name>Package</param-name>
            <param-value># Ajouter ici votre répertoire de package</param-value>
        </context-param>
    </web-app>
    ```

## Fonctionnalités

- **FrontController** : Le contrôleur principal qui capture l'URL de la requête et la redirige vers la méthode correspondante dans le bon contrôleur.
  
- **Annotations** :
  - `@Controller` : Utilisée pour marquer les classes comme contrôleurs.
  - `@RequestMapping` : Pour mapper des méthodes spécifiques aux URLs.
  - `@Param` : Pour injecter les paramètres des requêtes HTTP dans les méthodes des contrôleurs.
  - `@FieldParamName` : Permet de personnaliser les noms de champ des objets mappés aux formulaires.

- **`ModelView`** : Utilisé pour renvoyer des données et le nom de la vue JSP.
  
- **`RedirectView`** : Utilisé pour les redirections vers d'autres JSP.

- **Support des réponses JSON** : Si le retour d'une méthode n'est pas un `ModelView`, la réponse est automatiquement convertie en JSON à l'aide de la bibliothèque GSON.

## Exemple d'utilisation

### Classe `Employe`

```java
public class Employe {
    private String pseudo;
    private String password;

    // Getters et setters...
}
