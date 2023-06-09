# L'héritage
    Si une classe B herite d'une classe A cela veut dire que la classe B est la classe A car il elle herite de toutes les proriétés de la classe A

# L'aggregation
    - le nombre fait partie de l'objet
    - le membre peut appartenir a plusieurs objets a la fois
    - la creation du membre n'est pa géré par l'objet 
    
# Super()
    - utilisé pour appelé le constructeur du parent direct


# Les modificateurs d'accès 


                classe             package          sous-classe             globale
                                                    hors-package

private            v                    x               x                       x

default            v                    v               x                       x

protected          v                    v               v                       x

public              v                   v               v                       v

    private   : ce modificateurs n'est accessible que dans la classe
    default   : modificateur par defaut et n'est accessible que dans le package et la classe
    protected :  
    public    : accessible partout

    preference 
        -classe public ou default
        - champ private

# Abstraction
    C'est un processus qui consiste a masqué certain détails pour ne montrer que l'essentiel a l'utilisateur. Il se fait a travers un classe abstraite ou d'une interface

        Classe abstraite: 
                            -C'est une classe declarée avec le mot clé abstract ne peut pas être initialisé 
                            -qui peut avoir des méthodes non abstraite
                            -a au moins une méthode abstraite
                            -peut avoir des méthodes finales
                            -peut avoir des méthodes statics et un  constructeur

        Interface: represente le template ou le plan que doit suivre une classe 
                    Declaration : interface NomDel'interface (toujours en pascal case).
                                Il ne contient que des méthodes abstraites (bien qu'on ne met pas le mot abstract dans les interfaces)


# Java Enterprise Edition (J2EE)
    
    Pour que ça marche, on a besoin de Marvel+Appache Tomcat+jdk
        

    C'est une spéficité de java qui permet de faire des applis web.
    Elle est basée sur le MVC 
    En java le controller est appelé Servlet et le retour (vue) envoyé par le controller Java Server Pages (JSP)

    Le conteneur: Permet d'exécuter le code java compilé
         

## Le POM: 
    C'est un modèle d'objet de projet ou POM est l'unité de travail fondamentale de Maven. Il s'agit d'un fichier XML qui contient des informations sur le projet et les détails de configuration utilisés par Maven pour construire le projet. Il contient des valeurs par défaut pour la plupart des projets.
    
    Il contient quelques informations obligatoire:
        -project: c'est la racine du projet
        -modelVersion: doit être défini sur 4.0.0
        -groupId: c'est le nom du package (l'identifiant du groupe du projet)
        -artifacatId: l'identifiant de l'artefact (projet)
        -version: la version de l'artefact sous le groupe spécifié
    
    Après chaque modification il faut exécuter la commande mvn clean package


## Les objets implicites
    Ces objets sont créés par le conteneur Web et sont disponible pour toutes les pages jsp.  Il y en a 9:
        out, request, response, config, application, session, pageContext, page, exception

    Pour passer un attribut de la servle a la vue
        Dans la servlet: request.setAttribute("nomDeLaVariable","laValeur")
        Dans la vue: String NomVariable = (String (casting)) reqeust.getAttribut("nomDeLaVariable")

## Les expressions de language
    -Les directives jsp: 
        on les mets dans le <%@ %> . C'est une déclaration dans laquelle on met du code java
        Ex: include, pageEncoding.. il y en existe beaucoup
    -Les balises jsp: 
        on les mets dans le <% %> balises dans lequel on met le code source java
    
    La syntaxe: ${"NomDeLaVariable"} dans la vue affiche la variable correspondante

## Recupération des l'élements de l'url
    Syntax: ${param.nomDuParametre} 
        ou
        Dans la vue: String NomVariable = (String (casting)) reqeust.getParameter("nomDeLaVariable")

## Redirection en java
    req.SendRedirect("PageDeDestination")

## JSTL (Java server page Standard Tag Library)
    Représente un ensemble de balises pour simplifier le développement jsp.
    importation: <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>  

## Connection a la base de donnée avec java
	
    Cinq étapes importantes
	    -Enrégistrer la BDD de connection

            class.forName("com.mysql.jdbc.Driver")

	    -Récupérer l'objet de connection
            On utilise la méthode getConnection
            connection = DriverManager.getConnection("dsn", "Dbusername", "password")
                dsn: Data Source Name par exemple "jdbc:mysql://localhost:3306/user_db"
	    -Créer la requête
	    -Exécuter la requête
	    -Fermer la connexion

	La classe .forName
    -La DAO: L'Objet d'Accès aux Données

# SPRING BOOT
    (Si on a pas les extensions vscode ou un IDE java on peut passer par start.spring.io)
    En java le code est en .jar
    -Inversion de controle , injection de dépendance à l'intérieur du code grâce au pom.xml
    -Programation objet aspect(paradigme de programation qui permet de traiter séparement les préoccupations)
    -Couche d'abstraction

## Les annotations
    -Métadonnées incluses dans le code source
    -Utilisées avec quasiment tous les types d'entités
    -Précédé du caractère @

### Niveau de retention
    -Retention Policy.class: l'anotation est enrégistré dans le code 
    -Retention Policy.Rumtime: stocké et enrégistré dans la mémoire JVM lors de la compilation
    -Retention Policy.SOURCE: perdue aprés la compilation (ex: @getter @override)
### Cible et annotation
    -ElementType.TYPE: s'enploi sur une classe, une interface, une annotation ou un type énuméré 
    -ElementType.FIELD : s'enploi sur un attribut ou sur une constante d'un type énuméré
    -ElementType.METHOD: s'enploi sur une méthode (abstraite ou non, native ou non, statique ou non)
    -ElementType.CONSTRUCTOR: s'enploi sur un construteur
    -ElementType.LOCAL_VARIABLE: s'enploi sur une déclaration de variable locale a une méthode
    -ElementType.ANNOTATION_TYPE: s'enploi sur une autre annotation
    -ElementType.PACKAGE: s'enploi sur une declaration de paquetage
    -ElementType.PARAMETER: s'enploi sur une déclaration de type générique
    -ElementType.MODULE: s'enploi sur une définition de module
    --ElementType.TYPE_USE: s'enploi en mode extends

### Les types d'annotation
    - Les annotations standard: elles n'ont pa d'effets directs sur les entités qu'elles concernent (ex: @Deprecated, @Override, @SuppressWarnings)
    - Les annotations communes:
        - @Generated: permet de savoir que le code qui est en dessus a été généré par le framework
        - @Resource: definit une ressource requise par une classe. Par ex un composant Java EE de type EJB ou JMS 
        @Resource(name="MaQueue", type="javax.jms.Queue", shareable=false, auth...)

## Spring boot : Mise en place spring (configuration, pom.xml)

### Configuration

    Les etapes de la mise en place du projet
        -start.spring.io : télécharger le projet
        -commande: .\mvnw.cmd
        -commande: mvn clean
        -commande: mvn install
        -commande: mvn spring-boot:run qui envoi le serveur spring

### Pom.xml
    