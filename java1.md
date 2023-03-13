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