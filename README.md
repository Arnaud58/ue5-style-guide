# [Gamemakin](https://gamemak.in) UE5 Guide de Style() {

*Une approche plutôt raisonnable de l'Unreal Engine 5*

Fortement inspiré par le [Airbnb Javascript Style Guide](https://github.com/airbnb/javascript).

![](https://visitor-badge.glitch.me/badge?page_id=Arnaud58/ue5-style-guide)

## Notice du répo

Ce dépôt est maintenant situé à l'adresse https://github.com/Allar/ue5-style-guide. La branche par défaut de ce dépôt a été renommée en `main`.

## Ceci est actuellement pour UE4. Pour UE5/v2, voir la branche v2.
## Documentation sur Linter et le guide de style

Une documentation plus technique concernant Linter et le guide de style peut être trouvée sur notre page [ReadTheDocs](https://ue4-style-guide.readthedocs.io/en/latest/).

## A propos de ce guide stylistique

Gamemakin LLC dispose d'un channel public Discord à l'adresse http://discord.gamemak.in avec un canal #linter si vous souhaitez discuter de tout ce qui concerne le guide de style et le plugin Linter.

## Lien vers ce document

Chaque section de ce guide de style est numérotée pour faciliter les références et les liens. Vous pouvez créer un lien direct vers n'importe quelle section en ajoutant simplement une balise dièse et le numéro de la section à la fin de http://ue4.style.
Par exemple, si vous voulez envoyer quelqu'un au premier paragraphe de ce guide de style, vous devez ajouter `#0.1`, ce qui donne http://ue4.style#0.1.

## Forks et Traductions

Si vous avez créé un fork ou une traduction notable qui ne peut **pas** faire l'objet d'une demande de transfert dans ce dépôt, veuillez soumettre une *pull request* pour ajouter le fork ou la traduction ici.

* [Traduction coréenne](https://github.com/ymkim50/ue4-style-guide/blob/master/README_Kor.md) par ymkim50
* [Traduction en russe](https://github.com/CosmoMyzrailGorynych/ue4-style-guide-rus/blob/master/README.md) par CosmoMyzrailGorynych
* [Traduction japonaise](https://github.com/akenatsu/ue4-style-guide/blob/master/README.jp.md) par akenatsu
* [Traduction en chinois](https://github.com/skylens-inc/ue4-style-guide/blob/master/README.md) par Beijing Skylens Tech.
* [Traduction française](https://github.com/Arnaud58/ue5-style-guide/blob/main/README.md) par Arnaud58

## Terminologie importante

<a name="terms-level-map"></a>
##### Niveaux/Cartes

Le mot "Carte" (*map*) fait référence à ce qui est communément appelé "niveau" (*level*) dans UE4, et les deux termes sont synonymes. Voir l'historique de ce terme [ici](https://fr.wikipedia.org/wiki/Niveau_(jeu_vid%C3%A9o)). 

##### Identifiants
Un `Identifiant` est tout ce qui sert de "nom". Par exemple le nom d'un asset, d'un matériau, d'une propriété de blueprint, d'une variable, un nom de dossier, de ligne de table de données, etc....

<a name="terms-cases"></a>
##### Casses/Notations

Il y a plusieurs façons différentes dont vous pouvez `NoterLesMotsQuandNommer`. Voici quelques types de casses courantes :

> ###### PascalCase
>
> Met une majuscule à chaque mot et supprime tous les espaces, par exemple `DesertEagle`, `GuideDeStyle`, `UneSerieDeMots`.
> 
> ###### camelCase
>
> La première lettre est toujours en minuscule mais tous les mots suivants commencent par une majuscule, par exemple `desertEagle`, `guideDeStyle`, `uneSerieDeMots`.
>
> ###### Snake_case
>
> Les mots peuvent commencer arbitrairement en majuscules ou en minuscules mais les mots sont séparés par un trait de soulignement, par exemple `desert_Eagle`, `Guide_De_Style`, `une_Serie_de_Mots`.

<a name="terms-var-prop"></a>
##### Variables/Propriétés

Dans la plupart des contextes, les mots "variable" et "propriété" sont interchangeables. S'ils sont tous deux utilisés ensemble dans le même contexte cependant :

<a name="terms-property"></a>
###### Propriété 
Fait généralement référence à une variable définie dans une classe. Par exemple, si `BP_Tonneau` avait une variable `bExploser`, `bExploser` peut être désigné comme une propriété de `BP_Tonneau`. 

Dans le contexte d'une classe, il est souvent utilisé pour préciser l'accès à des données définies précédemment.

<a name="termes-variable"></a>
###### Variable 
Fait généralement référence à une variable définie comme un argument de fonction ou une variable locale à l'intérieur d'une fonction.

Lorsqu'il est dans le contexte d'une classe, il est souvent utilisé pour transmettre une information sur sa définition et sur son type.

<a name="0"></a>

## 0. Principes

Ces principes ont été adaptés du [guide de style idomatic JS](https://github.com/rwaldron/idiomatic.js/tree/master/translations/fr_FR).

<a name="0.1"></a>
### 0.1 Si votre projet UE4 suit déjà un guide de style, vous devez le suivre.

Si vous travaillez sur un projet ou avec une équipe qui a un guide de style préexistant, il faut le respecter. En cas d'incohérence entre un guide de style existant et le présent guide, il convient de s'en remettre au guide existant.

Les guides de style doivent être des documents évolutifs. Vous devez proposer des changements de style à un guide de style existant ainsi qu'à ce guide si vous pensez que le changement est bénéfique pour tous le monde.

> #### "Les arguments sur le style sont inutiles. Il devrait y avoir un guide de style, et vous devriez le suivre."
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 L'ensemble de la structure, des assets et du code de tout projet Unreal Engine 4 doit donner l'impression qu'une seule personne l'a créé, peu importe le nombre de personnes qui y ont contribué.

Passer d'un projet à un autre ne devrait pas entraîner un réapprentissage du style et de la structure. Le fait de se conformer à un guide de style élimine les approximations et les ambiguïtés inutiles.

Elle permet également une création et une maintenance plus productives, car il n'est pas nécessaire de réfléchir au style. Il suffit de suivre les instructions. Ce guide de style est écrit en tenant compte des meilleures pratiques, ce qui signifie qu'en suivant ce guide de style, vous minimiserez également les problèmes difficiles de maintenance de code.

<a name="0.3"></a>
### 0.3 Les amis ne laissent pas leurs amis avoir un mauvais style.

Si vous voyez quelqu'un travailler soit contre un guide de style, soit sans guide de style, essayez de le corriger.

Lorsque vous travaillez au sein d'une équipe ou discutez au sein d'une communauté telle que [Unreal Slackers](http://join.unrealslackers.org/), il est bien plus facile d'aider et de demander de l'aide lorsque les gens sont cohérents. Personne n'aime aider à démêler les spaghettis d'un Blueprint de quelqu'un d'autre ou de s'occuper d'assets dont les noms sont incompréhensibles.

Si vous aidez quelqu'un dont le travail est conforme à un guide de style différent mais cohérent et sain, vous devriez pouvoir vous y adapter. S'ils ne se conforment à aucun guide de style, veuillez les diriger ici.

<a name="0.4"></a>
### 0.4 Une équipe sans guide de style n'est pas mon équipe.

Lorsque vous rejoignez une équipe Unreal Engine 4, l'une de vos premières questions devrait être "Avez-vous un guide de style ?". Si la réponse est non, vous devriez être sceptique quant à leur capacité à travailler en équipe.

<a name="0.5"></a>
### 0.5 N'enfreignez pas la loi

Gamemakin LLC n'est pas un avocat, mais s'il vous plaît, n'introduisez pas d'actions et de comportements illégaux dans un projet, y compris mais sans s'y limiter :

* Ne distribuez pas de contenu dont vous n'avez pas les droits
* N'enfreignez pas les droits d'auteur ou les marques déposées de quelqu'un d'autre
* Ne pas voler de contenu
* Respecter les restrictions de licence sur le contenu, par exemple, citer quand les citations sont requises

<a name="00"></a>
## 00. Conseils Généraux

@TODO : Faire de cette section 1 et mettre à jour ce document en conséquence. ou pas ?

<a name="00.1"></a>
### 00.1 Caractères interdits

#### Identifiants

Dans tout `Identifiant` de quelque nature que ce soit, **ne jamais** utiliser les éléments suivants, à moins d'y être absolument contraint :

* Espace blanc de quelque nature que ce soit
* Des barres obliques inversées
* Symboles, par exemple `#!@$%`
* Tout caractère [Unicode](https://fr.wikipedia.org/wiki/Unicode)

Tout `Identifiant` devrait s'efforcer de n'avoir que les caractères suivants lorsque cela est possible (RegEx `[A-Za-z0-9_]+`)

* ABCDEFGHIJKLMNOPQRSTUVWXYZ
* abcdefghijklmnopqrstuvwxyz
* 1234567890
* _ (avec parcimonie)


Le raisonnement est le suivant : cela assurera la plus grande compatibilité de toutes les données sur toutes les plateformes à travers tous les outils, et aidera à prévenir les temps d'arrêt dus à une manipulation de caractères potentiellement mauvaise pour les identifiants dans le code que vous ne contrôlez pas.

<a name="table-of-contents"></a>
## Table des matières

> 1. [Conventions de dénomination des Assets](#anc)
> 1. [Structure du Répertoire](#structure)
> 1. [Blueprints](#bp)
> 1. [Static Meshes](#s)
> 1. [Systèmes de Particules](#ps)
> 1. [Niveaux/Cartes](#levels)
> 1. [Textures](#textures)

<a name="anc"></a>
<a name="1"></a>
## 1. Conventions de nommage des assets

Les conventions de nommage doivent être traitées comme des lois. Un projet qui se conforme à une convention de nommage est capable de gérer, rechercher, analyser et maintenir ses ressources avec une facilité incroyable.

La plupart des noms sont préfixées, les préfixes étant généralement un acronyme du type d'asset suivi d'un trait de soulignement.

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 Nom de base des Assets - `Prefix_NomBaseAsset_Varient_Suffix`.

Tous les assets doivent avoir un _Nom de base_. Un nom de base représente un regroupement d'assets apparentés. Tout assets faisant partie de ce groupe doit respecter la norme du`Prefix_NomBaseAsset_Varient_Suffix`.

Le bon sens et le modèle `Prefix_NomBaseAsset_Varient_Suffix` est généralement suffisant pour s'assurer de créer un bon nom d'asset. Voici quelques règles détaillées concernant chaque élément.

Le `Préfixe` et le `Suffixe` doivent être déterminés par le type d'asset à travers les tableaux suivantes [Modificateurs de Nom d'Asset](#asset-name-modifiers).

`NomBaseAsset` doit être un nom court et facilement reconnaissable lié au contexte de ce groupe d'asset. Par exemple, si vous avez un personnage nommé Bob, tous les asset de Bob auront pour `NomBaseAsset` `Bob`.

Pour les variations uniques et spécifiques des assets, `Varient` est un nom court et facilement reconnaissable qui représente un regroupement d'assets qui sont un sous-ensemble du nom de base d'un asset. Par exemple, si Bob a plusieurs skins, ces skins doivent toujours utiliser `Bob` comme `NomBaseAsset` mais inclure une `Varient` facilement reconnaissable. Un skin "Evil" sera appelé "Bob_Evil" et un skin "Retro" sera appelé "Bob_Retro".

Pour les variations uniques mais génériques des ressources, `Varient` est un nombre à deux chiffres commençant par `01`. Par exemple, si vous avez un artiste d'environnement qui génère des rochers, ils seront nommés `Rock_01`, `Rock_02`, `Rock_03`, etc. À part de rares exceptions, vous ne devriez jamais avoir besoin d'un numéro de varient à trois chiffres. Si vous avez plus de 100 assets, vous devriez envisager de les organiser avec des noms de base différents ou d'utiliser plusieurs noms de varients.

Selon la façon dont vos varients d'assets sont créées, vous pouvez enchaîner les noms de variantes. Par exemple, si vous créez des ressources de revêtement de sol pour un projet Arch Viz, vous devriez utiliser le nom de base `Flooring` avec des variantes enchaînées telles que `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

<a name="1.1-examples"></a>
#### 1.1 Exemples

##### 1.1e1 Bob

| Type d'Asset            | Nom de l'Asset                                             |
| ----------------------- | ---------------------------------------------------------- |
| Skeletal Mesh           | SK_Bob                                                     |
| Materiaux               | M_Bob                                                      |
| Texture (Diffuse/Albedo)| T_Bob_D                                                    |
| Texture (Normal)        | T_Bob_N                                                    |
| Texture (Evil Diffuse)  | T_Bob_Evil_D                                               |

##### 1.1e2 Rocks

| Type d'Asset            | Nom de l'Asset                                             |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | S_Rock_01                                                  |
| Static Mesh (02)        | S_Rock_02                                                  |
| Static Mesh (03)        | S_Rock_03                                                  |
| Material                | M_Rock                                                     |
| Material Instance (Snow)| MI_Rock_Snow                                               |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 Modificateur de Nom d'Asset

Lorsque vous nommez un asset, utilisez ces tableaux pour déterminer le préfixe et le suffixe à utiliser avec le [nom de base des assets](#base-asset-name).

#### Sections

> 1.2.1 [Les Plus Courant](#anc-common)

> 1.2.2 [Animations](#anc-animations)

> 1.2.3 [Intelligence Artificielle (I.A.)](#anc-ai)

> 1.2.4 [Blueprints](#anc-bp)

> 1.2.5 [Matériaux](#anc-materials)

> 1.2.6 [Textures](#anc-textures)

> 1.2.7 [Divers](#anc-misc)

> 1.2.8 [Paper 2D](#anc-paper2d)

> 1.2.9 [Physique](#anc-physics)

> 1.2.10 [Sons](#anc-sounds)

> 1.2.11 [Interface utilisateur](#anc-ui)

> 1.2.12 [Effets](#anc-effects)

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Les Plus Courant

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Map             |            |            | [Devrait se trouver dans un dossier appelé Maps ou Levels](#2.4) |
| Level (Persistent)      |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Lighting)        |            | _Lighting  |                                  |
| Level (Geometry)        |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Blueprint               | BP_        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | S_         |            | Beaucoup utilise SM_ Nous utilisons S_         |
| Skeletal Mesh           | SK_        |            |                                  |
| Texture                 | T_         | _?         | Voir [Textures](#anc-textures)    |
| Particle System         | PS_        |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 Animations

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Aim Offset              | AO_        |            |                                  |
| Aim Offset 1D           | AO_        |            |                                  |
| Animation Blueprint     | ABP_       |            |                                  |
| Animation Composite     | AC_        |            |                                  |
| Animation Montage       | AM_        |            |                                  |
| Animation Sequence      | A_         |            |                                  |
| Blend Space             | BS_        |            |                                  |
| Blend Space 1D          | BS_        |            |                                  |
| Level Sequence          | LS_        |            |                                  |
| Morph Target            | MT_        |            |                                  |
| Paper Flipbook          | PFB_       |            |                                  |
| Rig                     | Rig_       |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Skeleton                | SKEL_      |            |                                  |

<a name="anc-ai"></a>
<a name="1.2.3"></a>
### 1.2.3 Intelligence Artificielle (I.A.)

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_       |            |                                  |
| Behavior Tree           | BT_        |            |                                  |
| Blackboard              | BB_        |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_    |            |                                  |
| Environment Query       | EQS_       |            |                                  |
| EnvQueryContext         | EQS_       | Context    |                                  |

<a name="anc-bp"></a>
<a name="1.2.4"></a>
### 1.2.4 Blueprints

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Blueprint               | BP_        |            |                                  |
| Blueprint Component	  | BP_	       | Component  | Voir BP_InventoryComponent       |
| Blueprint Function Library | BPFL_   |            |                                  |
| Blueprint Interface     | BPI_       |            |                                  |
| Blueprint Macro Library | BPML_      |            | N'utilisez pas de bibliothèques de macro si possible |
| Enumeration             | E          |            | Pas d'underscore                 |
| Structure               | F or S     |            | Pas d'underscore                 |
| Tutorial Blueprint      | TBP_       |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.5"></a>
### 1.2.5 Materiaux

| Type d'Asset                  | Préfixe    | Suffixe    | Notes                            |
| ----------------------------- | ---------- | ---------- | -------------------------------- |
| Material                      | M_         |            |                                  |
| Material (Post Process)       | PP_        |            |                                  |
| Material Function             | MF_        |            |                                  |
| Material Instance             | MI_        |            |                                  |
| Material Parameter Collection | MPC_       |            |                                  |
| Subsurface Profile            | SP_        |            |                                  |
| Physical Materials            | PM_        |            |                                  |
| Decal                         | M_, MI_    | _Decal     |                                  |

<a name="anc-textures"></a>
<a name="1.2.6"></a>
### 1.2.6 Textures

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _O         |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Metallic)      | T_         | _M         |                                  |
| Texture (Packed)        | T_         | _*         | Voir notes à propos du [Regroupement](#anc-textures-packing). |
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Target           | RT_        |            |                                  |
| Cube Render Target      | RTC_       |            |                                  |
| Texture Light Profile   | TLP        |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.6.1"></a>
#### 1.2.6.1 Regroupement des textures
Il est courant de regrouper plusieurs couches de données d'un matériau dans une seule texture. Par exemple, l'ajout de l'Émissive (Emissive), de la Rugosité (Roughness) et de l'Occlusion ambiante (Ambient Occlusion) en tant que canaux rouge, vert, bleu d'une texture. Pour déterminer le suffixe, il suffit d'empiler les lettres des suffixe données ci-dessus, par exemple `_ERO`.

> Il est généralement acceptable d'inclure une couche Alpha/Opacité dans le canal alpha de votre Diffuse/Albedo et comme c'est une pratique courante, l'ajout de `A` au suffixe `_D` est facultatif.

Il n'est pas recommandé d'inclure 4 canaux de données dans une texture (RGBA), à l'exception d'un masque Alpha/Opacité dans le canal alpha du Diffuse/Albedo, car une texture avec un canal alpha est plus couteuse qu'une texture sans canal alpha.

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 Divers

| Type d'Asset               | Préfixe    | Suffixe    | Notes                            |
| -------------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field      | VFA_       |            |                                  |
| Camera Anim                | CA_        |            |                                  |
| Color Curve                | Curve_     | _Color     |                                  |
| Curve Table                | Curve_     | _Table     |                                  |
| Data Asset                 | *_         |            | Le préfixe doit être basé sur la classe |
| Data Table                 | DT_        |            |                                  |
| Float Curve                | Curve_     | _Float     |                                  |
| Foliage Type               | FT_        |            |                                  |
| Force Feedback Effect      | FFE_       |            |                                  |
| Landscape Grass Type       | LG_        |            |                                  |
| Landscape Layer            | LL_        |            |                                  |
| Matinee Data               | Matinee_   |            |                                  |
| Media Player               | MP_        |            |                                  |
| Object Library             | OL_        |            |                                  |
| Redirector                 |            |            | Devraient être réparés dès que possible   |
| Sprite Sheet               | SS_        |            |                                  |
| Static Vector Field        | VF_        |            |                                  |
| Substance Graph Instance   | SGI_       |            |                                  |
| Substance Instance Factory | SIF_       |            |                                  |
| Touch Interface Setup      | TI_        |            |                                  |
| Vector Curve               | Curve_     | _Vector    |                                  |

<a name="anc-paper2d"></a>
<a name="1.2.8"></a>
### 1.2.8 Paper 2D

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Paper Flipbook          | PFB_       |            |                                  |
| Sprite                  | SPR_       |            |                                  |
| Sprite Atlas Group      | SPRG_      |            |                                  |
| Tile Map                | TM_        |            |                                  |
| Tile Set                | TS_        |            |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
### 1.2.9 Physique

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Physics Asset	          | PHYS_      |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
### 1.2.10 Sons

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Dialogue Voice          | DV_        |            |                                  |
| Dialogue Wave           | DW_        |            |                                  |
| Media Sound Wave        | MSW_       |            |                                  |
| Reverb Effect           | Reverb_    |            |                                  |
| Sound Attenuation       | ATT_       |            |                                  |
| Sound Class             |            |            | Pas de préfixe/suffixe. Doit être placé dans un dossier appelé SoundClasses |
| Sound Concurrency       |            | _SC        | Doit être nommé d'après une SoundClasses |
| Sound Cue               | A_         | _Cue       |                                  |
| Sound Mix               | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 Interface utilisateur

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
### 1.2.12 Effets

| Type d'Asset            | Préfixe    | Suffixe    | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | PP_        |            |                                  |

**[⬆ Retourner à la table des matières](#table-of-contents)**


<a name="2"></a>
<a name="structure"></a>
## 2. Structure du Répertoire

Tout aussi important que les noms des assets, la manière de structurer le répertoire d'un projet doit être considéré faisant preuve de loi. Les conventions de nommage des assets et la structure des répertoires vont de pair, et une violation de l'une ou l'autre provoque un chaos important.

Il existe plusieurs façons de répartir le contenu d'un projet UE5. Dans ce style, nous préférons ici utilisé les capacités de filtrage et de recherche du navigateur de contenu afin de trouver des assets d'un type spécifique plutôt qu'une structure qui regroupe les assets de même types dans un même dossier.

> Si vous utilisez la préfixation comme [ci-dessus](#1.2), utiliser des dossiers qui contiennet des assets de types similaires tels que `Meshes`, `Textures` et `Matériaux` est redondant car les types d'asset sont déjà à la fois triés par préfixe et peuvent être filtrés par le navigateur de contenu.

<a name="2e1"><a>
### 2e1 Exemple de Structure de projet
<pre>
|-- Content
    |-- <a href="#2.2">GenericShooter</a>
        |-- Art
        |   |-- Industrial
        |   |   |-- Ambient
        |   |   |-- Machinery
        |   |   |-- Pipes
        |   |-- Nature
        |   |   |-- Ambient
        |   |   |-- Foliage
        |   |   |-- Rocks
        |   |   |-- Trees
        |   |-- Office
        |-- Characters
        |   |-- Bob
        |   |-- Common
        |   |   |-- <a href="#2.7">Animations</a>
        |   |   |-- Audio
        |   |-- Jack
        |   |-- Steve
        |   |-- <a href="#2.1.3">Zoe</a>
        |-- <a href="#2.5">Core</a>
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Weapons
        |-- Effects
        |   |-- Electrical
        |   |-- Fire
        |   |-- Weather
        |-- <a href="#2.4">Maps</a>
        |   |-- Campaign1
        |   |-- Campaign2
        |-- <a href="#2.8">MaterialLibrary</a>
        |   |-- Debug
        |   |-- Metal
        |   |-- Paint
        |   |-- Utility
        |   |-- Weathering
        |-- Placeables
        |   |-- Pickups
        |-- Weapons
            |-- Common
            |-- Pistols
            |   |-- DesertEagle
            |   |-- RocketPistol
            |-- Rifles
</pre>

Les raisons de cette structure sont énumérées dans les sous-sections suivantes.

### Sections

> 2.1 [Noms des dossiers](#structure-folder-names)

> 2.2 [Dossiers de premier niveau](#structure-top-level)

> 2.3 [Dossiers des développeurs](#structure-developers)

> 2.4 [Levels](#structure-maps)

> 2.5 [Core](#structure-core)

> 2.6 [`Assets` et `AssetTypes`](#structure-assettypes)

> 2.7 [Exeptions sur les grands assets](#structure-large-sets)

> 2.8 [Bibliothèque de Matériaux](#structure-material-library)

<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Noms de dossiers

Voici les règles communes pour nommer tout dossier dans la structure de contenu.

<a name="2.1.1"></a>
#### 2.1.1 Toujours utiliser le PascalCase [<sup>*</sup>](#terms-cases)

PascalCase consiste à commencer un nom par une majuscule, puis, au lieu d'utiliser des espaces, chaque mot suivant commence également par une majuscule. Par exemple, `DesertEagle`, `PistoletLaser`, et `UneSerieDeMots`.

Voir [Casses](#terms-cases).

<a name="2.1.2"></a>
#### 2.1.2 Ne jamais utiliser d'espaces

Pour renforcer [2.1.1](#2.1.1), n'utilisez jamais d'espaces. Les espaces peuvent faire échouer divers outils d'ingénierie et de scripts. Idéalement, la racine de votre projet ne contient pas non plus d'espaces et ressemble à `D:\Projet` plutot que `C:\Users\Mon Nom\Mes Documents\Unreal Projects`.

<a name="2.1.3"></a>
#### 2.1.3 Ne jamais utiliser de caractères Unicode et autres symboles

Si l'un des personnages de votre jeu s'appelle 'Zoë', le nom de son dossier doit être `Zoe`. Les caractères Unicode peuvent être pires que les [Espaces](#2.1.2) pour les outils d'ingénierie et certaines parties de UE4 et 5 ne supportent pas non plus les caractères Unicode dans les chemins.

Dans le même ordre d'idées, si votre projet présente des [problèmes inexpliqués](https://answers.unrealengine.com/questions/101207/undefined.html) et que le nom d'utilisateur de votre ordinateur comporte un caractère Unicode (c'est-à-dire que votre nom est `Zoë`), tout projet situé dans votre dossier `My Documents` souffrira de ce problème. Souvent, il suffit de déplacer votre projet dans un dossier tel que `D:\Project` pour résoudre ces problèmes mystérieux.

L'utilisation de caractères autres que `a-z`, `A-Z`, et `0-9` tels que `@`, `-`, `_`, `,`, `*`, et `#` peut également conduire à des problèmes inattendus et difficiles à suivre sur d'autres plateformes, contrôle de source, et outils d'ingénierie plus faibles. 

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Utiliser les dossier de premier niveau pour les ressources spécifiques au projet

Toutes les ressources d'un projet doivent se trouver dans un dossier portant le nom du projet. Par exemple, si votre projet s'appelle "Generic Shooter", _tout_ son contenu doit se trouver dans `Content/GenericShooter`.

> Le dossier `Developers` ne contient pas les ressources sur lesquelles votre projet repose, et n'est donc pas spécifique au projet. Voir [Developer Folders](#2.3) pour plus de détails à ce sujet.

Il y a de multiples raisons pour cette approche.

<a name="2.2.1"></a>
#### 2.2.1 Pas de biens globaux

Souvent dans les guides de style de code, il est écrit qu'il ne faut pas polluer l'espace de nom global et ceci suit le même principe. Lorsque les assets sont autorisés à exister en dehors d'un dossier de projet, il devient souvent beaucoup plus difficile de faire respecter une structure stricte, car les assets qui ne sont pas dans un dossier encouragent le mauvais comportement consistant à ne pas organiser les autres assets.

Chaque assets doit avoir un objectif, sinon il n'a pas sa place dans un projet. Si un assets est un test expérimental et ne doit pas être utilisé par le projet, il doit être placé dans un dossier [`Developer`](#2.3).

<a name="2.2.2"></a>
#### 2.2.2 Réduire les conflits de migration

Lorsqu'on travaille sur plusieurs projets, il est courant qu'une équipe copie des assets d'un projet à l'autre si elle a réalisé quelque chose de communs aux deux. Dans ce cas, la façon la plus simple d'effectuer la copie est d'utiliser la fonction Migrer du navigateur de contenu, car elle copie non seulement la ressource sélectionnée, mais aussi toutes ses dépendances.

Ce sont ces dépendances qui vont facilement vous causer des problèmes. Si les assets de deux projets n'ont pas de dossier de niveau supérieur et qu'ils ont des assets nommés de manière similaire ou déjà migrés, une nouvelle migration peut accidentellement effacer les modifications apportées aux assets existants.

C'est également la principale raison pour laquelle le personnel du marketplace d'Epic applique la même politique aux assets soumis.

Après une migration, les ressources peuvent être fusionnées en toute sécurité à l'aide de l'outil "Remplacer les références" du navigateur de contenu, avec la précision supplémentaire que les assets n'appartenant pas au dossier de premier niveau d'un projet sont clairement en attente de fusion. Une fois les ressources fusionnées et entièrement migrées, il ne devrait plus y avoir de dossier de premier niveau dans votre arborescence de contenu. Cette méthode est garantie à _100%_ pour que toutes les migrations qui se produisent soient totalement sûres.

<a name="2.2.2e1"></a>
##### 2.2.2e1 Exemple de "Master Material"

Supposons que vous ayez créé un "master material" dans un projet et que vous souhaitiez l'utiliser dans un autre projet, vous avez donc migré cet asset. Si cet asset n'est pas dans un dossier de niveau supérieur, il peut avoir un nom comme `Content/MaterialLibrary/M_Master`. Si le projet cible n'a pas déjà un "master material", cela devrait fonctionner sans problème.

Au fur et à mesure que le travail sur l'un ou les deux projets progresse, leurs "master material" respectifs peuvent être modifiés pour être adaptés à leurs projets spécifiques dans le cadre d'un développement normal.

Le problème se pose lorsque, par exemple, un artiste a créé pour un projet un bel ensemble modulaire générique de static meshes et que quelqu'un souhaite inclure cet ensemble de static meshes dans le second projet. Si l'artiste qui a créé les ressources a utilisé des instances de matériaux basées sur `Content/MaterialLibrary/M_Master` comme il en a reçu l'instruction, lorsqu'une migration est effectuée, il y a une grande chance de conflit pour la ressource `Content/MaterialLibrary/M_Master` précédemment migrée.

Ce problème peut être difficile à prévoir et à prendre en compte. La personne qui migre les static meshes peut ne pas être la même que celle qui est familière avec le développement du "master material" des deux projets, et elle peut même ne pas être consciente que les static meshes en question reposent sur des instances de matériau qui reposent ensuite sur le "master material". L'outil Migrate a cependant besoin de toute la chaîne de dépendances pour fonctionner, et il sera donc obligé de saisir `Content/MaterialLibrary/M_Master` lorsqu'il copiera ces assets vers l'autre projet et il écrasera l'asset existant.

C'est à ce moment-là que si les "master material" des deux projets sont incompatibles d'une manière ou d'une autre, vous risquez de casser toute la bibliothèque de matériaux d'un projet ainsi que toutes les autres dépendances qui ont déjà été migrées, simplement parce que les assets n'ont pas été stockés dans un dossier de niveau supérieur. La simple migration de static meshes devient maintenant une tâche très laide.

<a name="2.2.3"></a>
#### 2.2.3 Les Samples, Templates et le contenu du Marketplace sont sans risque.

Une extension de [2.2.2](#2.2.2), si un membre de l'équipe décide d'ajouter du contenu d'un Samples, des fichiers de Templates, ou des assets qu'ils ont achetés sur le marché, il est garanti, tant que le dossier de niveau supérieur de votre projet est nommé de manière unique, que ces nouveaux assets n'interféreront pas avec votre projet.

Vous ne pouvez pas faire confiance au contenu du Marketplace pour se conformer entièrement à la [règle du dossier de premier niveau](n° 2.2). Il existe de nombreuses ressources dont la majorité du contenu se trouve dans un dossier de premier niveau, mais qui contiennent également des échantillons de contenu Epic éventuellement modifiés ainsi que des fichiers de niveau polluant le dossier global `Content`.

En adhérant à [2.2](#2.2), le pire conflit du Marketplace que vous pouvez avoir est si deux assets utilisent le même Samples d'Epic. Si toutes vos ressources se trouvent dans un dossier spécifique au projet, y compris le contenu des Samples que vous avez déplacé dans votre dossier, votre projet ne sera jamais inquiété par les problèmes lié à l'importation d'assets.

#### 2.2.4 DLC, sous-projets et correctifs faciles à gérer

Si votre projet prévoit de publier un DLC ou s'il est associé à plusieurs sous-projets qui peuvent être transférés ou simplement ne pas être inclus lors d'une compilation, les ressources relatives à ces projets doivent avoir leur propre dossier de contenu de niveau supérieur. Cela facilite grandement la compilation du DLC séparément au contenu du projet principal. Les sous-projets peuvent également être migrés vers et hors du projet avec un minimum d'effort. Si vous devez modifier le matériau d'un asset ou ajouter un comportement très spécifique de remplacement d'asset dans un patch, vous pouvez facilement placer ces modifications dans un dossier de patch et travailler en toute sécurité sans risquer de casser le projet principal.

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Utiliser le dossier des développeurs pour les tests locaux

Au cours du développement d'un projet, il est très courant que les membres de l'équipe disposent d'une sorte de "bac à sable" où ils peuvent expérimenter librement sans risquer de compromettre le projet principal. Comme ce travail peut être continu, ces membres de l'équipe peuvent souhaiter placer leurs ressources sur le serveur de contrôle des sources du projet. Toutes les équipes n'ont pas besoin d'utiliser des dossiers de développeurs, mais celles qui le font rencontrent souvent un problème commun avec les ressources soumises au contrôle de source.

Il est très facile pour un membre de l'équipe d'utiliser accidentellement des ressources qui ne sont pas prêtes à être utilisées, ce qui causera des problèmes une fois ces ressources supprimées. Par exemple, un artiste peut être en train d'itérer sur un ensemble modulaire de Static Meshes et encore en train de travailler sur la dimension et le maillage du meshe. Si un Level Designer voit ces ressources dans le dossier principal du projet, il peut les utiliser dans tout le niveau sans savoir qu'elles peuvent être modifiées et/ou supprimées. Cela entraîne une quantité massive de retravail à résoudre pour tous les membres de l'équipe.

Si ces ressources modulaires étaient placées dans un dossier de développeur, le Level Designer n'aurait jamais eu de raison de les utiliser et le problème ne se serait jamais posé. Le navigateur de contenu dispose d'options d'affichage spécifiques qui masquent les dossiers Developer (ils sont masqués par défaut), ce qui rend impossible l'utilisation accidentelle des ressources Developer dans des conditions normales.

Une fois que les ressources sont prêtes à être utilisées, il suffit à l'artiste de les déplacer dans le dossier spécifique au projet et de corriger les redirecteurs. Il s'agit essentiellement de faire passer les ressources de la phase expérimentale à la phase de production.

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 Tous les fichiers Levels[<sup>*</sup>](#terms-level-map) appartiennent à un dossier appelé `Maps` 

Les fichiers de carte sont incroyablement spéciaux et il est courant que chaque projet ait son propre système de dénomination des cartes, surtout s'il travaille avec des sous-niveaux ou des streaming level. Quel que soit le système d'organisation des cartes mis en place pour un projet donné, tous les niveaux doivent se trouver dans le dossier `/Content/Project/Maps`.

Pouvoir dire à quelqu'un d'ouvrir une carte spécifique sans avoir à expliquer où elle se trouve est un grand gain de temps et une amélioration générale de la "qualité de vie". Il est courant que les niveaux se trouvent dans des sous-dossiers de `Maps`, comme `Maps/Campaign1/` ou `Maps/Arenas`, mais la chose la plus importante ici est qu'ils existent tous dans `/Content/Project/Maps`.

Cela simplifie également le travail de construction pour les ingénieurs. La manipulation des niveaux dans un processus de construction peut être extrêmement frustrante s'ils doivent fouiller dans des dossiers arbitraires pour les trouver. Si les cartes d'une équipe se trouvent toutes au même endroit, il est beaucoup plus difficile de ne pas compiller une carte par accident lors d'un build. Cela simplifie également les scripts de construction d'éclairage ainsi que les processus d'assurance qualité.

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 Utilisez un dossier `Core` pour les Blueprints critiques et autres actifs.

Utilisez le dossier `/Content/Project/Core` pour les actifs qui sont absolument fondamentaux pour le fonctionnement d'un projet. Par exemple, les Blueprints de base `GameMode`, `Character`, `PlayerController`, `GameState`, `PlayerState`, et les Blueprints associés devraient se trouver ici.

Cela crée un message très clair *"ne touchez pas à ça"* pour les autres membres de l'équipe. Les non-ingénieurs devraient avoir très peu de raisons d'entrer dans le dossier `Core`. En suivant le bon style de structure de code, les concepteurs devraient faire leurs modifications de gameplay dans les classes enfant qui exposent les fonctionnalités. Les Levels Designers devraient utiliser des Blueprints préfabriqués dans des dossiers désignés au lieu d'abuser potentiellement des classes de base.

Par exemple, si votre projet nécessite des collectables qui peuvent être placés dans un niveau, il devrait exister une classe de base Pickup (collectable en français) dans `Core/Pickups` qui définit le comportement de base pour un collectable. Des collectables spécifiques, tels que la santé ou les munitions, devraient exister dans un dossier tel que `/Content/Project/Placeables/Pickups/`. Les concepteurs de jeux peuvent définir et modifier les collectables dans ce dossier comme bon leur semble, mais ils ne doivent pas toucher à `Core/Pickups` car ils pourraient involontairement casser les collectables de tout le projet.

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Ne pas créer de dossiers appelés `Assets` ou `AssetTypes`.

<a name="2.6.1"></a>
#### 2.6.1 Créer un dossier nommé `Assets` est redondant.

**Tous les assets sont des assets.**

<a name="2.6.2"></a>
#### 2.6.2 Créer un dossier nommé `Meshes`, `Textures` ou `Matériaux` est redondant.

Tous les noms d'assets sont nommés en tenant compte du type d'asset. Ces dossiers n'offrent que des informations redondantes et l'utilisation de ces dossiers peut facilement être remplacée par le système de filtrage robuste et facile à utiliser que fournit le navigateur de contenu.

Vous voulez voir seulement les Static Mesh dans `Environnement/Rocks/` ? Activez simplement le filtre Static Mesh. Si tous les assets sont nommés correctement, ils seront également triés par ordre alphabétique, indépendamment des préfixes. Vous souhaitez afficher à la fois les Static Mesh et les Skeletals Meshes ? Il suffit d'activer les deux filtres. Ceci élimine le besoin de potentiellement devoir sélectionner deux dossiers dans l'arborescence du navigateur de contenu.

> Cela alonge également le nom du filepath de manière inutile. Le préfixe `S_` pour un Static Mesh n'a que deux caractères, alors que `Meshes/` en a sept.

Ne pas le faire permet également d'éviter que quelqu'un mette un Static Mesh ou une texture dans un dossier `Materials`.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Les très grands ensembles d'assets obtiennent leur propre disposition de dossiers.

Ceci peut être considéré comme une pseudo-exception à [2.6](#2.6).

Il y a certains types d'assets qui possèdent un énorme volume de fichiers liés où chaque asset a un but unique. Les deux plus cas les courants sont les assets d'animation et les assets audio. Si vous avez plus de 15 de ces ressources qui vont ensemble, elles doivent être regroupées.

Par exemple, les animations qui sont partagées par plusieurs personnages doivent être placées dans `Characters/Communs/Animations` et peuvent avoir des sous-dossiers tels que `Locomotion` ou `Cinematic`.

> Ceci ne s'applique pas aux assets tels que les textures et les matériaux. Il est courant qu'un dossier `Rocks` contienne une grande quantité de textures s'il y a une grande quantité de roches, cependant ces textures ne sont généralement liées qu'à quelques roches spécifiques et doivent être nommées de manière appropriée. Même si ces textures font partie d'une [Bibliothèque de Matériaux](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `Bibliothèque de Matériaux`

Si votre projet fait usage de "master materials", de "layered materials" ou de toute forme de matériaux ou de textures réutilisables qui n'appartiennent à aucun sous-ensemble d'assets, ces assets doivent être situés dans `Content/Project/MaterialLibrary`.

De cette façon, tous les matériaux "globaux" ont un endroit où vivre et sont facilement localisables.

> Cela rend également très facile l'application d'une politique d'utilisation exclusive des instances de matériaux dans un projet. Si tous les assets doivent utiliser des instances de matériaux, seul des instances de matériaux peuvent exister dans ce dossier. Vous pouvez facilement vérifier cela en recherchant les matériaux de base dans n'importe quel dossier qui n'est pas `MaterialLibrary`.

Le dossier `MaterialLibrary` n'est pas forcément composée uniquement de matériaux. Des textures utilitaires partagées, des "material functions" et d'autres choses de cette nature devraient être stockées ici aussi dans des dossiers qui désignent leur but. Par exemple, les textures de bruit devraient être situées dans `MaterialLibrary/Utility`.

Tous les matériaux de test ou de débogage doivent se trouver dans `MaterialLibrary/Debug`. Cela permet de retirer facilement les matériaux de débogage d'un projet avant de l'expédier et de voir clairement si les assets en production les utilisent en regardant si des erreurs de référence sont affichées.

<a name="2.9"></a>
<a name="structure-no-empty-folders"></a>
### 2.9 Pas de dossiers vides

Il ne devrait pas y avoir de dossiers vides. Ils encombrent le navigateur de contenu.

Si vous constatez que le navigateur de contenu contient un dossier vide que vous ne pouvez pas supprimer, procédez comme suit :
1. Vérifiez que vous utilisez le contrôle des sources.
1. Exécutez immédiatement "Fix Up Redirectors" sur votre projet.
1. Naviguez jusqu'au dossier sur le disque et supprimez les assets qui s'y trouvent.
1. Fermez l'éditeur.
1. Assurez-vous que l'état de votre contrôle de source est synchronisé (par exemple, si vous utilisez Perforce, exécutez un travail hors ligne de réconciliation sur votre répertoire de contenu).
1. Ouvrez l'éditeur. Confirmez que tout fonctionne comme prévu. Si ce n'est pas le cas, revenez en arrière, trouvez ce qui n'a pas fonctionné et réessayez.
1. Assurez-vous que le dossier a disparu.
1. Soumettre les changements au contrôle de source.

**[⬆ Retourner à la table des matières](#table-of-contents)**


<a name="3"></a>
<a name="bp"></a>
## 3. Blueprints

Cette section se concentre sur les Blueprint et leurs éléments internes. Dans la mesure du possible, les règles de style sont conformes au [Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

N'oubliez pas : le Blueprinting supporte mal les gaffes, méfiez-vous ! (Phrase de [KorkuVeren](http://github.com/KorkuVeren))

### Sections

> 3.1 [Compiling](#bp-compiling)

> 3.2 [Variables](#bp-vars)

> 3.3 [Functions](#bp-functions)

> 3.4 [Graphs](#bp-graphs)

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Compilation

Tous les blueprints doivent être compilés sans aucun avertissement ni aucune erreur. Vous devez corriger immédiatement les avertissements et les erreurs des blueprints car ils peuvent rapidement se transformer en un comportement inattendu très effrayant.

Ne soumettez *pas* les blueprints cassés au contrôle de source. Si vous devez les stocker dans le contrôle de source, mettez-les plutôt en attente.

Les blueprints cassés peuvent causer des problèmes qui se manifestent d'autres manières, comme des références cassées, un comportement inattendu, des échecs de compilation et des recompilations fréquentes et inutiles. Un blueprint cassé a le pouvoir de casser votre jeu entier.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Variables

Les mots `variable` et `propriété` peuvent être utilisés de manière interchangeable.

#### Sections

> 3.2.1 [Nommage](#bp-vars)

> 3.2.2 [Editable](#bp-vars-editable)

> 3.2.3 [Catégories](#bp-vars-categories)

> 3.2.4 [Accès](#bp-vars-access)

> 3.2.5 [Avancé](#bp-vars-advanced)

> 3.2.6 [Transitoire](#bp-vars-transitoire)

> 3.2.7 [Config](#bp-vars-config)

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Nommage

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 Noms

Tous les noms de variables non booléennes doivent être des substantifs clairs, non ambigus et descriptifs.

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 PascalCase

Toutes les variables non booléennes doivent être sous la forme [PascalCase](#terms-cases).

<a name="3.2.1.2e"></a>
###### 3.2.1.2e Exemples:

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3 Préfixe `b`

Tous les booléens doivent être nommés en PascalCase mais préfixés par un `b` minuscule.

Exemple : Utilisez `bDead` et `bEvil`, **et non** `Dead` et `Evil`.

Les éditeurs de Blueprint de UE4 savent qu'il ne faut pas inclure le `b` dans les affichages conviviaux de la variable.

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 Noms booléens

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1 Informations générales et indépendantes des états

Tous les booléens doivent être nommés comme des adjectifs descriptifs lorsque cela est possible s'ils représentent des informations générales. N'incluez pas les mots qui expriment la variable comme une question, tels que `Is`. Ceci est réservé aux fonctions.

Exemple : Utilisez `bDead` et `bHostile` **et non** `bIsDead` et `bIsHostile`.

Essayez de ne pas utiliser de verbes tels que `bRunning`. Les verbes ont tendance à conduire à des états complexes.

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 États complexes

Ne pas utiliser de booléens pour représenter des états complexes et/ou dépendants. Cela rend compliqué l'ajout et la suppression d'états et n'est pas facilement lisible. Utilisez plutôt une énumération dans ce cas là.

Exemple : Lors de la définition d'une arme, ne **pas** utiliser `bReloading` et `bEquipping` si une arme ne peut pas être à la fois rechargée et équipée. Définissez une énumération nommée `EWeaponState` et utilisez plutôt une variable de ce type nommée `WeaponState`. Cela rend beaucoup plus facile l'ajout de nouveaux états aux armes.

Exemple : Ne **pas** utiliser `bRunning` si vous avez aussi besoin de `bWalking` ou `bSprinting`. Cela devrait être défini comme une énumération avec des noms d'états clairement définis.

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Contexte considéré

Tous les noms de variables ne doivent pas être redondants avec leur contexte car toutes les références de variables dans Blueprint auront toujours un contexte.

<a name="3.2.1.5e"></a>
###### 3.2.1.5e Exemples:

Considérons un Blueprint appelé `BP_PlayerCharacter`.

**Mauvais**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

Toutes ces variables sont nommées de manière redondante. Il est sous-entendu que la variable est représentative du `BP_PlayerCharacter` auquel elle appartient car c'est `BP_PlayerCharacter` qui définit ces variables.

**Bon**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6 Ne _pas_ inclure les noms de types atomiques

Les variables atomiques ou primitives sont des variables qui représentent des données dans leur forme la plus simple, comme les booléens, les entiers, les flottants et les énumérations.

Les chaînes de caractères et les vecteurs sont considérés comme atomiques en termes de style lorsqu'on travaille avec Blueprints, mais ils ne le sont pas techniquement.

> Alors que les vecteurs sont composés de trois flottants, les vecteurs peuvent souvent être manipulés comme un tout, de même que les "Rotators".

> Ne considérez _pas_ les variables Text comme atomiques, elles cachent secrètement la fonctionnalité de localisation. Le type atomique d'une chaîne de caractères est `String`, pas `Text`.

Les variables atomiques ne doivent pas avoir leur nom de type dans leur nom.

Exemple : Utilisez `Score`, `Kills`, et `Description` **et non** `ScoreFloat`, `FloatKills`, `DescriptionString`.

La seule exception à cette règle est lorsqu'une variable représente "un nombre de" quelque chose à compter _et_ lorsque l'utilisation d'un nom sans type de variable n'est pas facile à lire.

Exemple : Un générateur de clôture doit générer un nombre X de poteaux. Enregistrez X dans `NumPosts` ou `PostsCount` au lieu de `Posts` car `Posts` peut potentiellement être lu comme un tableau d'un type de variable nommé `Post`.

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 Ne pas inclure les noms de types non atomiques

Les variables non atomiques ou complexes sont des variables qui représentent des données comme une collection de variables atomiques. Les structures, les classes, les interfaces et les primitives au comportement caché telles que `Text` et `Name` répondent toutes à cette règle.

> Alors qu'un tableau d'un type de variable atomique est une liste de variables, les tableaux ne modifient pas le caractère atomique d'un type de variable.

Ces variables doivent inclure leur nom de type tout en tenant compte de leur contexte.

Si une classe possède une instance d'une variable complexe, par exemple si un `BP_PlayerCharacter` possède un `BP_Hat`, elle doit être stockée comme type de variable sans modification de nom.

Exemple : Utilisez `Hat`, `Flag`, et `Ability` **et non** `MyHat`, `MyFlag`, et `PlayerAbility`.

Si une classe ne possède pas la variable qui est dans une variable complexe, vous devez compléter le nom avec le type de variable.

Exemple : Si une `BP_Turret` a la capacité de cibler un `BP_PlayerCharacter`, elle devrait stocker sa variable en tant que `TargetPlayer` car dans le contexte de `BP_Turret`, il devrait être clair qu'il s'agit d'une référence à un autre type de variable complexe qu'elle ne possède pas.


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Tableaux

Les tableaux suivent les mêmes règles de dénomination que ci-dessus, mais doivent être nommés comme un nom pluriel et être préfixé de `the`

Exemple : Utilisez `theTargets`, `theHats`, et `theEnemyPlayers`, **et non** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Variables modifiables

Toutes les variables dont on peut changer la valeur en toute sécurité afin de configurer le comportement d'un blueprint doivent être marquées comme `Editable`.

Inversement, toutes les variables que l'on est psa sûres de changer ou qui ne doivent pas être exposées aux concepteurs ne doivent pas être marquées comme modifiables, à moins que pour des raisons techniques, la variable doive être marquée comme `Expose On Spawn`.

Ne marquez pas arbitrairement les variables comme `Editable`.

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 Info-bulles

Toutes les variables `Editable`, y compris celles marquées editable juste pour qu'elles puissent être marquées comme `Expose On Spawn`, devraient avoir une description dans leurs champs `Tooltip` qui explique comment le changement de cette valeur affecte le comportement du blueprint.

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
<!-- https://forums.unrealengine.com/showthread.php?65227-Float-Variable-With-Slider-Range-From-C -->
##### 3.2.2.2 Curseur et plages de valeurs

Toutes les variables `Editable` devraient utiliser un curseur et une plage de valeurs s'il y a une valeur qui _ne devrait pas_ être définie pour cette variable.

Exemple : Si un blueprint qui génère des poteaux de clôture a une variable éditable `PostsCount`, cela n'aurait pas de sens de pouvoir lui donner une valeur de -1. Utilisez le champ plage pour définir 0 comme valeur minimale.

Si la variable modifiable est utilisée dans un script de construction, il convient de définir une plage de curseurs appropriée afin d'éviter de définir accidentellement une valeur si grande qu'elle fait planter l'éditeur.

Une plage de valeurs ne doit être définie que si les limites de la valeur sont connues. La plage de valeurs du curseur empêche la saisie accidentelle d'un trop grand nombre de valeurs, mais une plage de valeurs non définies peut être utilisée pour spécifier des valeurs en dehors de la plage du curseur. Cette valeur est considérée comme "dangereuse" mais elle est toujours valable.

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Catégorie

Si une classe comporte un petit nombre de variables, l'utilisation de catégories n'est pas obligatoire.

Si une classe a un nombre modéré de variables (5-10), toutes les variables `Editable` se verront attribuer une catégorie autre que celle par défaut. Une catégorie commune à assigner est `Config`.

Si une classe a un grand nombre de variables, toutes les variables `éditables` doivent être classées en sous-catégories en utilisant la catégorie `Config` comme catégorie de base. Les variables non modifiables doivent être classées dans une catégorie descriptive décrivant leur utilisation.

> Les sous-catégories peuvent être définies en utilisant le caractère pipe `|`. c'est-à-dire `Config | Animations`.

Exemple : Une configuration variable pour une classe d'arme peut être structurée comme suit :

	|-- Config
	|	|-- Animations
	|	|-- Effects
	|	|-- Audio
	|	|-- Recoil
	|	|-- Timings
	|-- Animations
	|-- State
	|-- Visuals

<a name="3.2.4"></a>
<a name="bp-vars-access"></a>
#### 3.2.4  Niveau d'accès variable 

En C++, les variables ont le concept de niveaux d'accès. Public signifie que du code extérieur à la classe peut accéder à la variable. Protégé signifie que seule la classe et toutes les classes filles peuvent accéder à cette variable en interne. Privé signifie que seule cette classe et aucune classe enfant n'a accès à cette variable.

Les Blueprints ne définissent pas actuellement le concept de contrôle de l'accès à Protected.

Les variables `Editable` sont traitées comme des variables publiques. Traiter les variables non éditables comme des variables protégées.

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 Variables privées

Ne marquez pas une variable comme privée à moins qu'elle ne soit utilisée uniquement au sein de la classe dans laquelle elle est définie et qu'elle ne soit pas utilisé dans une classe enfant. Gardez les variables privées jusqu'à ce qu'elles soient marquées `protégées`, ceci est à faire quand vous savez absolument que vous voulez restreindre leur utilisation aux classes enfants.

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 Affichage avancé

Si une variable est `Editable`, mais que vous ne changez pas souvent sa valeur, vous devriez cocher la case `Advanced Display`. La variable sera ainsi masquée, sauf si vous cliquez sur la flèche d'affichage étendu.

Pour rechercher l'option `Advanced Display`, elle apparaîtra dans la liste détaillée des variables en tant que `Advanced Display`.

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 Variables temporaires

Une variable temporaire est une variable qui a une valeur initiale à zéro ou null, sans qu'il soit nécessaire de sauvegarder et de charger la valeur. Ceci est utile pour les références à d'autres objets ou acteurs dont les valeurs ne sont pas connues avant l'exécution. Cela empêche l'éditeur d'enregistrer cette référence et accélère l'enregistrement et le chargement des classes Blueprint.
	
Pour cette raison, toutes les variables temporaires doivent toujours être initialisées à zéro ou à une valeur nulle. Sinon, il sera difficile de déboguer les erreurs.

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.7 Variables de configuration

L'indicateur `Config Variable` ne doit pas être utilisé. Celà rend difficile pour le concepteur de contrôler le comportement du blueprint. Les variables de configuration ne doivent être utilisées en C++ que pour les variables qui sont rarement modifiées. Considérez-les comme des variables d'`affichage très très avancé`.

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 Functions, Events, and Event Dispatchers

This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Function Naming

The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Is it a pure function?
* Is it fetching state information?
* Is it a handler?
* Is it an RPC?
* What is its purpose?

These questions and more can all be answered when functions are named appropriately.

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 All Functions Should Be Verbs

All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should all start with verbs. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

`OnRep` functions, event handlers, and event dispatchers are an exception to this rule.

Good examples:

* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `Jump` - Good example if in a Character class, otherwise, needs context.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:

* `Dead` - Is Dead? Will deaden?
* `Rock`
* `ProcessData` - Ambiguous, these words mean nothing.
* `PlayerState` - Nouns are ambiguous.
* `Color` - Verb with no context, or ambiguous noun.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`

All functions for replicated with notification variables should have the form `OnRep_Variable`. This is forced by the Blueprint editor. If you are writing a C++ `OnRep` function however, it should also follow this convention when exposing it to Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Info Functions Returning Bool Should Ask Questions

When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow [the verb rule](#bp-funcs-naming-verbs).

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

Good examples:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" is past-tense of "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" when referring to 'previous frame' or 'previous state'.
* `CanReload` - ["Can" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Bad examples:

* `Fire` - Is on fire? Will fire? Do fire?
* `OnFire` - Can be confused with event dispatcher for firing.
* `Dead` - Is dead? Will deaden?
* `Visibility` - Is visible? Set visibility? A description of flying conditions?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers and Dispatchers Should Start With `On`

Any function that handles an event or dispatches an event should start with `On` and continue to follow [the verb rule](#bp-funcs-naming-verbs). The verb may move to the end however if past-tense reads better.

[Collocations](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) of the word `On` are exempt from following the verb rule.

`Handle` is not allowed. It is 'Unreal' to use `On` instead of `Handle`, while other frameworks may prefer to use `Handle` instead of `On`.

Good examples:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Bad examples:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target

Any time an RPC is created, it should be prefixed with either `Server`, `Client`, or `Multicast`. No exceptions.

After the prefix, follow all other rules regarding function naming.

Good examples:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Bad examples:

* `FireWeapon` - Does not indicate its an RPC of some kind.
* `ServerClientBroadcast` - Confusing.
* `AllNotifyDeath` - Use `Multicast`, never `All`.
* `ClientWeapon` - No verb, ambiguous.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 All Functions Must Have Return Nodes

All functions must have return nodes, no exceptions.

Return nodes explicitly note that a function has finished its execution. In a world where blueprints can be filled with `Sequence`, `ForLoopWithBreak`, and backwards reroute nodes, explicit execution flow is important for readability, maintenance, and easier debugging.

The Blueprint compiler is able to follow the flow of execution and will warn you if there is a branch of your code with an unhandled return or bad flow if you use return nodes.

In situations like where a programmer may add a pin to a Sequence node or add logic after a for loop completes but the loop iteration might return early, this can often result in an accidental error in code flow. The warnings the Blueprint compiler will alert everyone of these issues immediately.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 No Function Should Have More Than 50 Nodes

Simply, no function should have more than 50 nodes. Any function this big should be broken down into smaller functions for readability and ease of maintenance.

The following nodes are not counted as they are deemed to not increase function complexity:

* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 All Public Functions Should Have A Description

This rule applies more to public facing or marketplace blueprints, so that others can more easily navigate and consume your blueprint API.

Simply, any function that has an access specificer of Public should have its description filled out. 

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name

If your project includes a plugin that defines `static` `BlueprintCallable` functions, they should have their category set to the plugin's name or a subset category of the plugin's name.

For example, `Zed Camera Interface` or `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs

This section covers things that apply to all Blueprint graphs.

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 No Spaghetti

Wires should have clear beginnings and ends. You should never have to mentally untangle wires to make sense of a graph. Many of the following sections are dedicated to reducing spaghetti.

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Align Wires Not Nodes

Always align wires, not nodes. You can't always control the size and pin location on a node, but you can always control the location of a node and thus control the wires. Straight wires provide clear linear flow. Wiggly wires wear wits wickedly. You can straighten wires by using the Straighten Connections command with BP nodes selected. Hotkey: Q

Good example: The tops of the nodes are staggered to keep a perfectly straight white exec line.
![Aligned By Wires](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-good.png "Aligned By Wires")

Bad Example: The tops of the nodes are aligned creating a wiggly white exec line.
![Bad](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-bad.png "Wiggly")

Acceptable Example: Certain nodes might not cooperate no matter how you use the alignment tools. In this situation, try to minimize the wiggle by bringing the node in closer.
![Acceptable](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-acceptable.png "Acceptable")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 White Exec Lines Are Top Priority

If you ever have to decide between straightening a linear white exec line or straightening data lines of some kind, always straighten the white exec line.

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Graphs Should Be Reasonably Commented

Blocks of nodes should be wrapped in comments that describe their higher-level behavior. While every function should be well named so that each individual node is easily readable and understandable, groups of nodes contributing to a purpose should have their purpose described in a comment block. If a function does not have many blocks of nodes and its clear that the nodes are serving a direct purpose in the function's goal, then they do not need to be commented as the function name and  description should suffice.

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Graphs Should Handle Casting Errors Where Appropriate

If a function or event assumes that a cast always succeeds, it should appropriately report a failure in logic if the cast fails. This lets others know why something that is 'supposed to work' doesn't. A function should also attempt a graceful recover after a failed cast if it's known that the reference being casted could ever fail to be casted.

This does not mean every cast node should have its failure handled. In many cases, especially events regarding things like collisions, it is expected that execution flow terminates on a failed cast quietly.

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Graphs Should Not Have Any Dangling / Loose / Dead Nodes

All nodes in all blueprint graphs must have a purpose. You should not leave dangling blueprint nodes around that have no purpose or are not executed.

**[⬆ Retourner à la table des matières](#table-of-contents)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Static Meshes

This section will focus on Static Mesh assets and their internals.

### Sections

> 4.1 [UVs](#s-uvs)

> 4.2 [LODs](#s-lods)

> 4.3 [Modular Socketless Snapping](#s-modular-snapping)

> 4.4 [Must Have Collision](#s-collision)

> 4.5 [Correct Scale](#s-scaled)

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

If Linter is reporting bad UVs and you can't seem to track it down, open the resulting `.log` file in your project's `Saved/Logs` folder for exact details as to why it's failing. I am hoping to include these messages in the Lint report in the future.

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 All Meshes Must Have UVs

Pretty simple. All meshes, regardless how they are to be used, should not be missing UVs.

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps

Pretty simple. All meshes, regardless how they are to be used, should have valid non-overlapping UVs.

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs Should Be Set Up Correctly

This is a subjective check on a per-project basis, but as a general rule any mesh that can be seen at varying distances should have proper LODs.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Modular Socketless Assets Should Snap To The Grid Cleanly

This is a subjective check on a per-asset basis, however any modular socketless assets should snap together cleanly based on the project's grid settings.

It is up to the project whether to snap based on a power of 2 grid or on a base 10 grid. However if you are authoring modular socketless assets for the marketplace, Epic's requirement is that they snap cleanly when the grid is set to 10 units or bigger.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 All Meshes Must Have Collision

Regardless of whether an asset is going to be used for collision in a level, all meshes should have proper collision defined. This helps the engine with things such as bounds calculations, occlusion, and lighting. Collision should also be well-formed to the asset.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 All Meshes Should Be Scaled Correctly

This is a subjective check on a per-project basis, however all assets should be scaled correctly to their project. Level designers or blueprint authors should not have to tweak the scale of meshes to get them to confirm in the editor. Scaling meshes in the engine should be treated as a scale override, not a scale correction.

**[⬆ Retourner à la table des matières](#table-of-contents)**


<a name="5"></a>
<a name="Niagara"></a>
<a name="ng"></a>
## 5. Niagara

This section will focus on Niagara assets and their internals.

### Sections

> 5.1 [Naming Rules](#ng-rules)

<a name="5.1"></a>
<a name="ng-rules"></a>
### 5.1 No Spaces, Ever

As mentioned in [00.1 Forbidden Identifiers](#00), spaces and all white space characters are forbidden in identifiers. This is especially true for Niagara systems as it makes working with things significantly harder if not impossible when working with HLSL or other means of scripting within Niagara and trying to reference an identifier.

(Original Contribution by [@dunenkoff](https://github.com/Allar/ue5-style-guide/issues/58))


**[⬆ Retourner à la table des matières](#table-of-contents)**


<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels / Maps

[See Terminology Note](#terms-level-map) regarding "levels" vs "maps".

This section will focus on Level assets and their internals.

### Sections

> 6.1 [No Errors Or Warnings](#levels-no-errors-or-warnings)

> 6.2 [Lighting Should Be Built](#levels-lighting-should-be-built)

> 6.3 [No Player Visible Z Fighting](#evels-no-visible-z-fighting)

> 6.4 [Marketplace Specific Rules](#evels-levels-mp-rules)

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 No Errors Or Warnings

All levels should load with zero errors or warnings. If a level loads with any errors or warnings, they should be fixed immediately to prevent cascading issues.

You can run a map check on an open level in the editor by using the console command "map check".

Please note: Linter is even more strict on this than the editor is currently, and will catch load errors that the editor will resolve on its own.

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 Lighting Should Be Built

It is normal during development for levels to occasionally not have lighting built. When doing a test/internal/shipping build or any build that is to be distributed however, lighting should always be built.

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 No Player Visible Z Fighting

Levels should not have any [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) in all areas visible to the player. 

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 Marketplace Specific Rules

If a project is to be sold on the UE4 Marketplace, it must follow these rules.

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
### 6.4.1 Overview Level

If your project contains assets that should be visualized or demoed, you must have a map within your project that contains the name "Overview".

This overview map, if it is visualizing assets, should be set up according to [Epic's guidelines](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps).

For example, `InteractionComponent_Overview`.

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
### 6.4.2 Demo Level

If your project contains assets that should be demoed or come with some sort of tutorial, you must have a map within your project that contains the name "Demo". This level should also contain documentation within it in some form that illustrates how to use your project. See Epic's Content Examples project for good examples on how to do this.

If your project is a gameplay mechanic or other form of system as opposed to an art pack, this can be the same as your "Overview" map.

For example, `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Retourner à la table des matières](#table-of-contents)**


<a name="7"></a>
<a name="textures"></a>
## 7. Textures

This section will focus on Texture assets and their internals.

### Sections

> 7.1 [Dimensions Are Powers of 2](#textures-dimension)

> 7.2 [Texture Density Should Be Uniform](#textures-dimension)

> 7.3 [Textures Should Be No Bigger than 8192](#textures-max-size)

> 7.4 [Correct Texture Groups](#textures-textures-group)

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Dimensions Are Powers of 2

All textures, except for UI textures, must have its dimensions in multiples of powers of 2. Textures do not have to be square.

For example, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 Texture Density Should Be Uniform

All textures should be of a size appropriate for their standard use case. Appropriate texture density varies from project to project, but all textures within that project should have a consistent density.

For example, if a project's texture density is 8 pixel per 1 unit, a texture that is meant to be applied to a 100x100 unit cube should be 1024x1024, as that is the closest power of 2 that matches the project's texture density. 

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 Textures Should Be No Bigger than 8192

No texture should have a dimension that exceeds 8192 in size, unless you have a very explicit reason to do so. Often, using a texture this big is simply just a waste of resources.

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 Textures Should Be Grouped Correctly

Every texture has a Texture Group property used for LODing, and this should be set correctly based on its use. For example, all UI textures should belong in the UI texture group.

**[⬆ Retourner à la table des matières](#table-of-contents)**


## Major Contributors

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Retourner à la table des matières](#table-of-contents)**


## Amendments

We encourage you to fork this guide and change the rules to fit your team's style guide. Below, you may list some amendments to the style guide. This allows you to periodically update your style guide without having to deal with merge conflicts.

# };
