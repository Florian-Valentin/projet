## Rapport séance 6 :

Lors de cette séance, nous avons repris là où nous nous étions arrêté. Pour ma part, je voulais réussir à faire fonctionner les servo moteur sour l'IDE MaixPy.
Après de nombreuses recherches, j'ai trouvé l'erreur lié au "board.PIN2". Il n'y avait aucune problème de code, ou de nouelles versions.
Simplement, avant de comencer à utiliser la PWM sur cet IDE, il fait executer un code que l'on retrouve grâce au lien suivant.

https://wiki.sipeed.com/soft/maixpy/en/get_started/board_info.html

Le fait d'executer ce code, va permettre une "mise à niveau" de notre IDE, ce qui va lui permettre d'utiliser la PWM correctement.
Une fois que le code "MaixDuino" a été executé, les les codes de la semaines dernières pouvaient enfin s'executer correctement.

Les moteurs étant enfin opérationnel, je me suis penché sur le modèle que nous avons créer.
Nous savons utiliser une modèle type sur internet, cependant les modèles crées sur MAIXHUB sont moins facile à utiliser.

> Lors de la prochaine séance, nous allons essayer de faire fonctionner un de nos modèle.
