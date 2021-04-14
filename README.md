# React avec TypeScript: bonnes pratiques

React et TypeScript sont deux technologies géniales utilisées par de nombreux développeurs ces jours-ci. Savoir comment faire les choses peut devenir délicat, et parfois il est difficile de trouver la bonne réponse. Ne pas s'inquiéter. Nous avons rassemblé les meilleures pratiques ainsi que des exemples pour clarifier les doutes que vous pourriez avoir.

## Comment React et TypeScript fonctionnent ensemble

Avant de commencer, revoyons comment React et TypeScript fonctionnent ensemble. **React** est une **«bibliothèque JavaScript pour la création d'interfaces utilisateur»**, tandis que **TypeScript** est un **«sur-ensemble typé de JavaScript qui se compile en JavaScript brut»**. En les utilisant ensemble, nous construisons essentiellement nos interfaces utilisateur en utilisant une version typée de JavaScript.

La raison pour laquelle vous pourriez les utiliser ensemble serait d'obtenir les avantages d'un langage à typage statique (TypeScript) pour votre interface utilisateur. Cela signifie plus de sécurité et moins de bogues expédiés à l'avant.

## TypeScript compile-t-il mon code React?

Une question courante qu'il est toujours bon d'examiner est de savoir si TypeScript compile votre code React. Le fonctionnement de TypeScript est similaire à cette interaction:<br/>

**TS**: "Hé, est-ce tout votre code d'interface utilisateur?"<br/>
**React**: "Ouais!"
**TS**: «Cool! Je vais le compiler et m'assurer que vous n'avez rien manqué. "
**React**: "Ça me semble bien!"


La réponse est donc oui! Mais plus tard, lorsque nous aborderons les paramètres **tsconfig.json**, la plupart du temps, vous souhaiterez utiliser **"noEmit": true**. Cela signifie que **TypeScript** n'émettra pas de JavaScript après la compilation. En effet, généralement, nous n'utilisons que **TypeScript** pour effectuer notre vérification de type.

La sortie est gérée, dans un cadre **CRA**, par **react-scripts**. Nous exécutons **yarn build** et **react-scripts** pour regroupe la sortie pour la production.

>Pour récapituler, TypeScript compile votre code React pour vérifier le type de votre code. Il n'émet aucune sortie JavaScript (dans la plupart des scénarios). La sortie est toujours similaire à un projet React non TypeScript.

## TypeScript peut-il fonctionner avec React et Webpack?

Oui, TypeScript peut fonctionner avec React et webpack. Heureusement pour vous, la documentation du Webpack contient un [guide](https://webpack.js.org/guides/typescript/) à ce sujet.

J'espère que cela vous donnera un léger rappel sur la façon dont les deux fonctionnent ensemble. Maintenant, passons aux meilleures pratiques!