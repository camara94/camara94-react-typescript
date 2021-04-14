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

## Les meilleures pratiques

L'une des parties du développement les moins amusantes mais les plus importantes est la configuration. Comment pouvons-nous mettre en place les choses dans les plus brefs délais pour offrir une efficacité et une productivité maximales? Nous aborderons la configuration du projet, notamment:

* <code>tsconfig.json</code>
* ESLint
* Prettier
* VS Code extensions and settings.

## Configuration du projet
Le moyen le plus rapide de démarrer une application **React / TypeScript** consiste à utiliser <code>create-react-app</code> avec le modèle TypeScript. Vous pouvez le faire en exécutant:

<code>npx create-react-app guinnea-market --template typescript</code>

Cela vous donnera le strict minimum pour commencer à écrire React avec TypeScript. Quelques différences notables sont:

* l'extension de fichier <code>.tsx</code>
* le <code>tsconfig.json</code>
* le <code>react-app-env.d.ts</code>

Le tsx est pour «TypeScript JSX». Le <code>tsconfig.json</code> est le fichier de configuration TypeScript, dont certaines valeurs par défaut sont définies. Le <code>react-app-env.d.ts</code> fait référence aux types de <code>react-scripts</code>, et aide par exemple à autoriser les importations SVG

### tsconfig.json
Heureusement pour nous, le dernier modèle **React / TypeScript** génère <code>tsconfig.json</code> pour nous. Cependant, ils ajoutent le strict minimum pour commencer. Nous vous suggérons de modifier le vôtre pour qu'il corresponde à celui ci-dessous. Nous avons ajouté des commentaires pour expliquer également le but de chaque option:<br/>

<code>
    <pre>
        {
        "compilerOptions": {
            "target": "es5", // Specify ECMAScript target version
            "lib": [
            "dom",
            "dom.iterable",
            "esnext"
            ], // List of library files to be included in the compilation
            "allowJs": true, // Allow JavaScript files to be compiled
            "skipLibCheck": true, // Skip type checking of all declaration files
            "esModuleInterop": true, // Disables namespace imports (import * as fs from "fs") and enables CJS/AMD/UMD style imports (import fs from "fs")
            "allowSyntheticDefaultImports": true, // Allow default imports from modules with no default export
            "strict": true, // Enable all strict type checking options
            "forceConsistentCasingInFileNames": true, // Disallow inconsistently-cased references to the same file.
            "module": "esnext", // Specify module code generation
            "moduleResolution": "node", // Resolve modules using Node.js style
            "isolatedModules": true, // Unconditionally emit imports for unresolved files
            "resolveJsonModule": true, // Include modules imported with .json extension
            "noEmit": true, // Do not emit output (meaning do not compile code, only perform type checking)
            "jsx": "react", // Support JSX in .tsx files
            "sourceMap": true, // Generate corrresponding .map file
            "declaration": true, // Generate corresponding .d.ts file
            "noUnusedLocals": true, // Report errors on unused locals
            "noUnusedParameters": true, // Report errors on unused parameters
            "incremental": true, // Enable incremental compilation by reading/writing information from prior compilations to a file on disk
            "noFallthroughCasesInSwitch": true // Report errors for fallthrough cases in switch statement
        },
        "include": [
            "src/**/*" // *** The files TypeScript should type check ***
        ],
        "exclude": ["node_modules", "build"] // *** The files to not type check ***
        }
    </pre>
</code>