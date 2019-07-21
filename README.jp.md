# [Gamemakin](https://gamemak.in) UE4スタイルガイド() {

*そこそこ妥当なUnreal Engine 4 へのアプローチ*

本ガイドは、 [Airbnb Javascript スタイルガイド](https://github.com/airbnb/javascript) に多大な影響を受けています。

[![Analytics](https://ga-beacon.appspot.com/UA-80567399-1/repo?useReferrer)](#) ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

## Unreal Engine 4 Linter Plugin

あなたのプロジェクトが本スタイルガイドに準じているか自動的にチェックする手段は、 [the Unreal Engine marketplace](https://www.unrealengine.com/marketplace/linter) で購入できます。 このプラグインのソースコードは最終的に無料になりますが、UE4をソースコードからビルドせずに使用したい場合は、マーケットプレイス版の使用をお勧めします。

## 本スタイルガイドについて議論するには

Gamemakin LLCは、Discordの http://discord.gamemak.in にpublicチャンネルを持っており、スタイルガイドとLinterプラグインに関するあらゆる事について、議論したい場合は #linter チャンネルを利用してください。 

## 本ドキュメントへリンクする場合には

本スタイルガイドの全てのセクションは、参照とリンクの利便性ために番号が振られています。 http://ue4.style の末尾にハッシュタグとセクション番号を付け足すだけで、特定のセクションに直接リンクができます
たとえば、このスタイルガイドの原則、第一節へのリンクを誰かに教えたい場合は、 http://ue4.style#0.1 という風に `＃0.1` を追加しましょう。

## フォークと翻訳

本githubリポジトリへのプルリクエストにはそぐいませんが、素晴らしいフォーク、または翻訳を行った場合は、以下にそのフォークまたは翻訳へのリンクを追加するプルリクエストの提出をお願いします。

* [Korean Translation](https://github.com/ymkim50/ue4-style-guide/blob/master/README_Kor.md) by ymkim50
* [Russian Translation](https://github.com/CosmoMyzrailGorynych/ue4-style-guide-rus/blob/master/README.md) by CosmoMyzrailGorynych
* [Japanese Translation](https://github.com/akenatsu/ue4-style-guide/blob/master/README.jp.md) by akenatsu
* [Chinese Translation](https://github.com/skylens-inc/ue4-style-guide/blob/master/README.md) by Beijing Skylens Tech.

## 重要用語　

<a name="terms-level-map"></a>
##### Levels/Maps

ゲームのワールドマップ(以下 'map') は、一般にUE4で 'level' と呼んでいるものを指していて、どちらの用語も多分同じ意味で使えます。この用語の歴史的経緯については[こちら](https://en.wikipedia.org/wiki/Level_(video_gaming))を参照してください。

<a name="terms-cases"></a>
##### 記法(Cases)

命名法にはいくつかのバリエーションがあります。 以下に一般的な記法を幾つか紹介します:

> ###### PascalCase
>
> 全単語の最初を大文字で、スペースは使わない。例： `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.
> 
> ###### camelCase
>
> 最初の単語は小文字で、残りの単語の最初を大文字で。例： `desertEagle`, `styleGuide`, `aSeriesOfWords`.
>
> ###### Snake_case
>
> 各単語は任意で大文字または小文字始まり、全ての単語間はアンダースコアで区切る。例： `desert_Eagle`, `Style_Guide`, `a_Series_of_Words`.

<a name="terms-var-prop"></a> 
##### 変数/プロパティ(属性) (Variables / Properties)

ほとんどのコンテキスト(文脈)において、 '変数' と 'プロパティ' は同じ意味で使われます。 ただし、両方が同一コンテキスト上で使用されている場合においてのみ、使用可能です：

<a name="terms-property"></a> 
###### プロパティ (Properties)
通常、クラス内で定義された変数を指します。 たとえば、`BP_Barrel` ブループリントクラスに `bExploded` 変数がある場合、 `bExploded` は `BP_Barrel` クラスのプロパティと呼ばれます。

クラスのコンテキスト内では、前もって定義したデータにアクセスできることを示すためによく使用されます。

<a name="terms-variable"></a> 
###### 変数 (Variables)
通常は、関数の引数または関数内のローカル変数で定義された変数を指します。 

クラスのコンテキスト内では、変数自身の定義とその変数が保持する何かについての議論を円滑にするために、よく使用されます。 

<a name="0"></a>
## 0. 原則　

これらの原則は [idomatic.js style guide](https://github.com/rwaldron/idiomatic.js/) に即しています。

<a name="0.1"></a>
### 0.1 あなたのUE4プロジェクトにすでにスタイルガイドがある場合は、それに従うべき

既にスタイルガイドを持っているチームまたはプロジェクトで作業する場合は、それを尊重する必要があります。既存のスタイルガイドとこのガイドとの間に不一致がある場合は、既存のスタイルガイドに従わなくてはなりません。

とはいえスタイルガイドは生きたドキュメントでなければなりません。全ての用途で変更にメリットがあると感じたら、既存のスタイルガイドに本ガイド同様の変更を加えるよう提案するべきです。

> #### "スタイルに関して議論することに意味はありません。スタイルガイドありきで、それに従うべきなのです"
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 どのUE4プロジェクトでも、どんなに多くの人が貢献したとしても、全ての(ディレクトリ)構造、アセット、およびコードは、1人で作成したように見えるようにするべき

別のプロジェクトに移動しても、そちらでスタイルや(ディレクトリ)構造の再学習が発生しないようにするべきです。 スタイルガイドに従うことで、不必要な推測や曖昧さがなくなります。

また単にスタイルガイドに従えば、スタイルについて考えなる必要がなくなることにより、生産的な創作と保守が可能です。 このスタイルガイドはベストプラクティスを念頭に置いて書かれています。つまり、このスタイルガイドに従えば、問題を追跡する労力を最小限に抑えることができるのです。

<a name="0.3"></a>
### 0.3 チームのメンバの悪いスタイルを律するべき

スタイルガイドに反していたりスタイルガイド無しで作業している人がいる場合は指導するようにしてください。

チーム内で作業したり、 [Unreal Slackers](http://join.unrealslackers.org/ ) などのコミュニティで議論するときは、一貫性があれば助けたり助けを求めたりがはるかに簡単になります。 誰も、他人のブループリントのスパゲッティを解くのを手伝ったり、理解できない名前のアセットを扱ったりはしたくないのです。

あなたが手伝っている人の作品が異なったスタイルガイドに即したものでも、それに一貫性があり真っ当なスタイルガイドならば、あなたはそれに適応できるはずです。 彼らがなんのスタイルガイドにも従っていない場合は、ここへ案内してください。

<a name="0.4"></a>
### 0.4 スタイルガイドの無いチームは、チームでは無い

UE4チームに参加するとき、最初にすべき質問の1つは「あなたたちはスタイルガイドを持っていますか？」です。 答えがノーなら、彼らのチームとして作業する能力について疑問を持たなければなりません。

<a name="0.5"></a>
### 0.5 法律を破るな

Gamemakin LLC は弁護士では無いです。ですが、どうぞプロジェクトへの不正な行動や振る舞いを取り込まないでください。以下に限定されるものではありませんが:

* 配布権を有さないコンテンツを配布しないこと
* 他人の著作権及び商標権を害さないこと
* コンテンツを盗まないこと
* コンテンツのライセンス規約に従うこと(例え. 帰属することが必要とされる属性の場合)

<a name="toc"></a>
<a name="table-of-contents"></a>
## 目次　

> 1. [アセット命名規則](#anc)
> 1. [コンテンツディレクトリ構成](#structure)
> 1. [ブループリント](#bp)
> 1. [スタティックメッシュ](#s) 
> 1. [パーティクルシステム](#ps) 
> 1. [レベルとマップ](#levels) 
> 1. [テクスチャ](#textures) 

<a name="anc"></a>
<a name="1"></a>
## 1. アセットの命名規則について ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

(( [アセットの命名規則 ](https://wiki.unrealengine.com/Assets_Naming_Convention_JP) ))

命名規則は、法律のように扱うべきです。 命名規則に準拠したプロジェクトでは、アセットの管理、検索、解析、保守が非常に簡単です。

ほとんどのものに接頭辞(Prefix)が付いています。接頭辞は一般的にアセットタイプの略語で、その後にアンダースコアが続きます。

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 基本アセット名　 - `Prefix_BaseAssetName_Variant_Suffix` ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

すべてのアセットに _基本アセット名_ _(Base Asset Name)_ が必要です。基本アセット名は、関連するアセットの論理的なグループを表します。この論理グループの一部であるアセットは、 `Prefix_BaseAssetName_Variant_Suffix`(接頭辞にアセットタイプを、接尾辞に種類を)の標準に従うべきです。

パターン `Prefix_BaseAssetName_Variant_Suffix` を念頭に置いて常識的に使えば、一般的に良いアセット名であることが十分に保証されます。各要素に関するいくつかの詳細なルールをここで見ましょう。

`Prefix`と` Suffix`は、以下の [Asset Name Modifier](#asset-name-modifiers) テーブルより、アセットタイプによって決定されます。

`BaseAssetName` は、このアセット群の文脈に関連した簡単で分かりやすい名前によって決定されるべきです。たとえば、Bobという名前のキャラクターがいた場合、Bobに関する全てのアセットで `BaseAssetName` は `Bob` になります。

ユニークでかつ特殊なアセットのバリエーションの場合、 `Variant` は、アセットの基本名のサブセットであるアセットの論理的なグループ分けを表す簡単で分かりやすい名前のいずれかです。例えば、Bobが複数のスキンを持っていた場合、これらのスキンは `BaseAssetName`として`Bob`を使用しますが、認識可能な `Variant`を含みます。 「Evil」スキンは `Bob_Evil` と呼ばれ、「Retro」スキンは `Bob_Retro` と呼ばれます。

ユニークではあるが汎用なアセットのバリエーションでは、 `Variant` は `01` から始まる2桁の数字です。例えば、岩石を作成する背景アーティストがいる場合、名前は `Rock_01`、` Rock_02`、 `Rock_03` などとなります。まれな例外を除いて、バリアントに3桁の数字は必要ありません。アセットが100以上ある場合は、異なるベース名で複数のバリアント名を使用して整理することを検討する必要があります。

アセットバリアントの作成方法に応じて、バリアント名を連結することができます。たとえば、Arch Vizプロジェクトのフロアリングアセットを作成する場合は、`Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01` などの連鎖バリアントを含むベース名 `Flooring` を使用する必要があります。

<a name="1.1-examples"></a>
#### 1.1 例　

##### 1.1e1 Bob((キャラクター、人物、動物など))

| Asset Type              | Asset Name                                                 |
| ----------------------- | ---------------------------------------------------------- |
| Skeletal Mesh           | SK_Bob                                                     |
| Material                | M_Bob                                                      |
| Texture (Diffuse/Albedo)| T_Bob_D                                                    |
| Texture (Normal)        | T_Bob_N                                                    |
| Texture (Evil Diffuse)  | T_Bob_Evil_D                                               |

##### 1.1e2 Rocks((静物、背景オブジェクトなど))

| Asset Type              | Asset Name                                                 |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | S_Rock_01                                                  |
| Static Mesh (02)        | S_Rock_02                                                  |
| Static Mesh (03)        | S_Rock_03                                                  |
| Material                | M_Rock                                                     |
| Material Instance (Snow)| MI_Rock_Snow                                               |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 アセット名修飾子　　![#](https://img.shields.io/badge/lint-supported-green.svg)

アセットの名前を付けるときは、これらのテーブルを使用してアセットの　[基本アセット名](#base-asset-name)　で使用する接頭辞(Prefix)と接尾辞(Suffix)を決定します。

#### セクション

> 1.2.1 [共通項目(Most Common)](#anc-common)

> 1.2.2 [アニメーション(Animations)](#anc-animations)

> 1.2.3 [人工知能(Artificial Intelligence)](#anc-ai)

> 1.2.4 [ブループリント(Blueprint)](#anc-bp)

> 1.2.5 [マテリアル(Materials)](#anc-materials)

> 1.2.6 [テクスチャ(Textures)](#anc-textures)

> 1.2.7 [その他(Miscellaneous)](#anc-misc)

> 1.2.8 [Paper 2D](#anc-paper2d)

> 1.2.9 [物理(Physics)](#anc-physics)

> 1.2.10 [サウンド(Sound)](#anc-sounds)

> 1.2.11 [UI(User Interface)](#anc-ui)

> 1.2.12 [エフェクト(Effects)](#anc-effects)

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Most Common ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Map             |            |            | [ Mapsフォルダ配下に置くべき.](#2.4) |
| Level (Persistent)      |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Lighting)        |            | _Lighting  |                                  |
| Level (Geometry)        |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Blueprint               | BP_        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | S_         |            | SM_ がよく使用されるが、 我々は S_ を推奨する |
| Skeletal Mesh           | SK_        |            |                                  |
| Texture                 | T_         | _?         | [Textures](#anc-textures) を参照   |
| Particle System         | PS_        |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |
 
<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 Animations ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
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
### 1.2.3 Artificial Intelligence ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
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
### 1.2.4 Blueprint ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Blueprint               | BP_        |            |                                  |
| Blueprint Componet      | BP_        | Component  | 即ち BP_InventoryComponent       |
| Blueprint Function Library | BPFL_   |            |                                  |
| Blueprint Interface     | BPI_       |            |                                  |
| Blueprint Macro Library | BPML_      |            | 可能な限り、マクロライブラリは使わない。 |
| Enumeration             | E          |            | アンダースコアを付けない。         |
| Structure               | F or S     |            | アンダースコアを付けない。         |
| Tutorial Blueprint      | TBP_       |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.5"></a>
### 1.2.5 Materials ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type                    | Prefix     | Suffix     | 注意(Notes)                      |
| -----------------------       | ---------- | ---------- | -------------------------------- |
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
### 1.2.6 Textures ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
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
| Texture (Packed)        | T_         | _*         | 下記の注記 [packing](#anc-textures-packing) を参照 　|
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Target           | RT_        |            |                                  |
| Cube Render Target      | RTC_       |            |                                  |
| Texture Light Profile   | TLP        |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.6.1"></a>
#### 1.2.6.1 Texture Packing ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

テクスチャデータの複数レイヤは1つのテクスチャにパックするのが一般的な方法です。 これの一例は、発光（エミッシブ）、粗さ（ラフネス）、環境遮蔽（アンビエントオクルージョン）をテクスチャの赤、緑、青のチャンネルとしてまとめたものです。 接尾辞を決定するには、上の指定された接尾辞の文字を単純に重ねます。 `_ERO`。

> Diffuse/AlbedoのアルファチャンネルにAlpha/Opacityレイヤーを含めることは一般的に受け入れられています。これは一般的な方法なので、 接尾辞`_D` に ` A` を付加するかどうかは好きにしてください。

Diffuse/AlbedoのアルファチャンネルにAlpha/Opacityマスクを含める場をを除いて、アルファチャネルを含むテクスチャは無いものに比べてオーバヘッドが大きいので、4チャンネルのデータをテクスチャ（RGBA）にパッキングするのはお勧めできません。

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 Miscellaneous ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field   | VFA_       |            |                                  |
| Camera Anim             | CA_        |            |                                  |
| Color Curve             | Curve_     | _Color     |                                  |
| Curve Table             | Curve_     | _Table     |                                  |
| Data Asset              | *_         |            | 接頭辞はクラスに基づいている必要があります |
| Data Table              | DT_        |            |                                  |
| Float Curve             | Curve_     | _Float     |                                  |
| Foliage Type            | FT_        |            |                                  |
| Force Feedback Effect   | FFE_       |            |                                  |
| Landscape Grass Type    | LG_        |            |                                  |
| Landscape Layer         | LL_        |            |                                  |
| Matinee Data            | Matinee_   |            |                                  |
| Media Player            | MP_        |            |                                  |
| Object Library          | OL_        |            |                                  |
| Redirector              |            |            | これらはできるだけ早く修正する必要があります |
| Sprite Sheet            | SS_        |            |                                  |
| Static Vector Field     | VF_        |            |                                  |
| Touch Interface Setup   | TI_        |            |                                  |
| Vector Curve            | Curve_     | _Vector    |                                  |

<a name="anc-paper2d"></a>
<a name="1.2.8"></a>
### 1.2.8 Paper 2D ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Paper Flipbook          | PFB_       |            |                                  |
| Sprite                  | SPR_       |            |                                  |
| Sprite Atlas Group      | SPRG_      |            |                                  |
| Tile Map                | TM_        |            |                                  |
| Tile Set                | TS_        |            |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
### 1.2.9 Physics ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Physical Asset	  | PHYS_      |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
### 1.2.10 Sounds ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Dialogue Voice          | DV_        |            |                                  |
| Dialogue Wave           | DW_        |            |                                  |
| Media Sound Wave        | MSW_       |            |                                  |
| Reverb Effect           | Reverb_    |            |                                  |
| Sound Attenuation       | ATT_       |            |                                  |
| Sound Class             |            |            | 接頭辞/接尾辞を付けません。 SoundClassesフォルダ配下に置べき　 |
| Sound Concurrency       |            | _SC        | SoundClassの後に名前付けるべき 　|
| Sound Cue               | A_         | _Cue       |                                  |
| Sound Mix               | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 User Interface ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
### 1.2.12 Effects ![#](https://img.shields.io/badge/lint-supported-green.svg)

| Asset Type              | Prefix     | Suffix     | 注意(Notes)                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | PP_        |            |                                  |

**[⬆ Back to Top](#table-of-contents)**


<a name="2"></a>
<a name="structure"></a>
## 2. コンテンツディレクトリの構成について ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)
 
アセット名と同様に重要なことに、プロジェクトのディレクトリ構造のスタイルも法律のように扱うべきです。 アセットの命名規則とコンテンツディレクトリ構造が両立しなければ、どちらかの違反は片手落ちとなり不要な混乱の原因となります。

UE4プロジェクトのコンテンツレイアウトは幾つかの方法があります。 本ガイドのスタイルでは、アセットタイプのグループ化などの他の共通構造としてフォルダを使った方法の代わりに、特定のタイプのアセットを検索するために、コンテンツブラウザのフィルタリングと検索機能にもっと依存する構造を使用します。

> 上記の [命名規則](#1.2) の接頭辞(prefix)を使用している場合、フォルダを使って `Meshes`, `Textures`, および `Materials`などの類似の型のアセットを格納することは、冗長です。アセットタイプがすでに両方とも接頭辞(prefix)でソートされているため、コンテンツブラウザでフィルタリングすることができます。


<a name="2e1"><a>
### 2e1 プロジェクトのコンテンツ構造の例　
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

このフォルダ構造の理由は、以下のサブセクションに記載します。

### セクション

> 2.1 [フォルダ名](#structure-folder-names)

> 2.2 [トップレベルのフォルダ](#structure-top-level)

> 2.3 [Developers フォルダ](#structure-developers)

> 2.4 [Maps フォルダ](#structure-maps)

> 2.5 [Core フォルダ](#structure-core)

> 2.6 [`Assets` と `AssetTypes`](#structure-assettypes)

> 2.7 [巨大アセットセット](#structure-large-sets)

> 2.8 [Material ライブラリ](#structure-material-library)


<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1  フォルダ名　 ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

以下はコンテンツディレクトリ構造での、任意のフォルダへの名前付けの共通ルールです。

<a name="2.1.1"></a>
#### 2.1.1 常に PascalCase を使うこと [<sup>*</sup>](#terms-cases) ![#](https://img.shields.io/badge/lint-supported-green.svg)

PascalCaseは、大文字で名前を始めることを意味し、スペースを使用する代わりに、すべての次の単語も大文字で始まります。 たとえば、`DesertEagle`, `RocketPistol`,および `ASeriesOfWords` などです。

[記法](#terms-cases)を参照。

<a name="2.1.2"></a>
#### 2.1.2 絶対にスペースを使わないこと ![#](https://img.shields.io/badge/lint-supported-green.svg)

[常に PascalCase を使うこと](#2.1.1) を再徹底したうえで、絶対にスペースを使わないでください。 スペースによって、さまざまな開発ツールやバッチ処理などで失敗する可能性があります。 プロジェクトのルートには空白が含まれておらず、 `C:\Users\My Name\My Documents\Unreal Projects` の代わりに `D:\Project`のような場所に置かれているのが理想的です。

<a name="2.1.3"></a>
#### 2.1.3 絶対にUnicodeと他の記号を使わないこと ![#](https://img.shields.io/badge/lint-supported-green.svg)

あなたのゲームキャラクターの名前が「Zoë」の場合、そのフォルダ名は `Zoe` にするべきです。 Unicodeは、UE4の解説ツール等ではパス(path)にUnicode文字を含むことをサポート [スペース](#2.1.2) より悪くなることがあります。

これに関連して、プロジェクトに [不可解な問題](https://answers.unrealengine.com/questions/101207/undefined.html) がある場合、コンピュータのユーザー名がUnicode文字（つまり、あなたの名前は `Zoë`）である場合や、 `My Documents`フォルダ以下にUE4プロジェクトを置いている場合は、これらの問題に苦しんでいる場合、 ただ単にUE4プロジェクトを `D:\Project` などに移動するだけで、これらの摩訶不思議な問題が解決するでしょう。

`@`, `-`, `_`, `,`, `*`, と `#` のような `a-z`, `A-Z`, 及び `0-9` 以外の文字を使うことによる、 他のプラットフォーム、ソース管理、および脆弱な解析ツールから問題を追跡することは困難です。

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 プロジェクト固有アセットには、トップレベルのフォルダを使うこと ![#](https://img.shields.io/badge/lint-supported-green.svg)

全てのプロジェクトアセットは、プロジェクトと同名フォルダ以下に置くべきです。 たとえば、プロジェクト名が「Generic Shooter」の場合、そのコンテンツの _全て_ は `Content/GenericShooter` 以下に配置する必要があります。

> `Developers` フォルダは、プロジェクトに依存しているアセット用ではない、つまりプロジェクト固有のものではありません。 これに関する詳細は [Developers フォルダ](#2.3) を参照してください。

このアプローチには幾つかの理由があります。

<a name="2.2.1"></a>
#### 2.2.1 グローバルアセットは作成しないこと

ほかの多くのコードスタイルガイドでも、グローバル名前空間を汚染しない事、と書かれています。このガイドも同じ原則に従います。 アセットがプロジェクトフォルダの外部に存在することが許可してしまう場合、プロジェクトフォルダ内にないアセットは整理する必要がないという悪い行為を促すため、厳密な構造レイアウトを強制することが困難になります。

すべてのアセットは目的を持っている必要があります。そうでなければ、プロジェクトに属していません。 アセットが実験的なテストであり、プロジェクトで使用すべきでない場合は、 [`Developers`](#2.3) フォルダに置く必要があります。 

<a name="2.2.2"></a>
#### 2.2.2 移行時の衝突の削減
<!-- todo review -->
複数のプロジェクトに取り組んでいるときに、２つのプロジェクトに役立つものを作っていれば、プロジェクト間でそのアセットをコピーするのがチームにとって一般的です。このようなとき、コピーを実行する最も簡単な方法は、コンテンツブラウザの移行機能を使用することです。それは選択したアセットだけでなく、同時に依存関係にあるアセットもすべてコピーします。

これらの依存関係は容易に問題を発生させ得るものです。 2つのプロジェクトのアセットにトップレベルのフォルダがなく、同様の名前が付けられているか、すでに以前に移行されたアセットがある場合は、新しい移行によって既存のアセットの変更がうっかり消し去られる可能性があります。

これはEpicのMarketplaceスタッフが提出されたアセットに対して同じポリシーを強制する主要な理由にもなっています。

移行後にコンテンツブラウザの '参照の置き換え(Replace References)' ツールを使用すると、明らかにマージを保留していて、プロジェクトのトップレベルのフォルダに属していないアセットの明確さを向上させ、アセットの安全なマージが可能になります。ひとたびアセットがマージされ、完全に移行されると、コンテンツツリーに別のトップレベルのフォルダは存在しないはずです。この方法は、完全に安全な移行を行うことを _100％_ 保証しています。

<a name="2.2.2e1"></a>
##### 2.2.2e1 マスターマテリアルの例　

たとえば、あるプロジェクトに別のプロジェクトで使用したいマスターマテリアルを作成し、そのアセットを移行したとします。このアセットがトップレベルのフォルダにない場合、 `Content/MaterialLibrary/M_Master` のような名前を持つ可能性があります。ターゲットプロジェクトにまだマスタマテリアルがない場合、これは問題なく動作するはずです。

一方または両方のプロジェクトの作業が進行するにつれて、それぞれのマスターマテリアルは、正規の開発過程のせいで、特定のプロジェクトに合わせて変更される可能性があります。

たとえば、あるプロジェクトのアーティストが静的メッシュ用の汎用的なモジュラーセットを作成し、誰かがその静的メッシュのセットを2番目のプロジェクトに含める場合など、問題が発生します。アセットを作成したアーティストが、指示されているとおりに `Content/MaterialLibrary/M_Master` に基づいてマテリアルインスタンスを使用した場合、移行が実行されると、以前に移行された `Content/MaterialLibrary/M_Master` のアセットとぶつかる能性が高くなります。

この問題は、予測するのも説明するのも難しい場合があります。静的メッシュを移動する人は、プロジェクトのマスターマテリアルの開発に精通している人と同じ人ではないかもしれませんし、問題の静的メッシュがマスターマテリアルに依存しているマテリアルインスタンスに依存していることに気づいていないかもしれません。しかし、移行ツールでは、依存関係のチェーン全体が機能する必要があるため、これらのアセットを他のプロジェクトにコピーするときに `Content/MaterialLibrary/M_Master`を強制的に取得し、既存のアセットを上書きします。

この時点で、いずれにせよ両方のプロジェクトのマスタマテリアルが互換性がない場合は、プロジェクトのマテリアルライブラリ全体や、すでに移行されている可能性のあるその他の依存関係を壊す可能性があります。これはアセットがトップレベルのフォルダに格納されていないためです。静的メッシュの単純な移行は、今や非常に危険な作業になっています。

<a name="2.2.3"></a>
#### 2.2.3 サンプル、テンプレート、マーケットプレイスのコンテンツはノーリスクです

[移行時の衝突の削減](#2.2.2) の拡張版では、チームメンバーがサンプルコンテンツ、テンプレートファイル、またはマーケットプレイスから購入したアセットを追加することを決定した場合、プロジェクトのトップレベルフォルダに一意の名前が付けられていれば、プロジェクトで新しいアセットと干渉し合わないことが保証されます。

マーケットプレイスのコンテンツが [トップレベルのフォルダルール](#2.2) に完全に準拠していると思ってはいけません。トップレベルのフォルダに大半のコンテンツを持つアセットが多く存在しますが、もしかするとレベルファイルがグローバル `Content` フォルダを汚染するのと同様にEpicのサンプルコンテンツも変更されている可能性があります。

[トップレベルのフォルダ](#2.2) を遵守する場合の最悪のマーケットプレイスの競合は、2つのマーケットプレイスアセットがともに同じEpicサンプルコンテンツを持つ場合に起こります。プロジェクトに移動したかもしれないサンプルコンテンツも含めて、すべてのアセットがプロジェクト固有のフォルダに含まれている場合、プロジェクトは決して壊れません。

#### 2.2.4 DLC((ダウンロードコンテンツ))、サブプロジェクト、およびパッチは簡単に維持できます

プロジェクトをDLCにリリースする予定があるか、または複数のサブプロジェクトが関連付けられていて、他のプロジェクトは移行されるか、単にビルドがクックされていない場合、これらのプロジェクトに関連するアセットは、独自に別々のトップレベルコンテンツフォルダが必要です。これにより、メインプロジェクトのコンテンツとは独立してDLCをクックすることがはるかに簡単になります。サブプロジェクトを、最小限の労力でイン／アウトすることもできます。アセットのマテリアルを変更したり、パッチにおける振る舞いをオーバーライドする非常に特殊なアセットを追加する必要がある場合は、これらの変更をパッチフォルダに加えることは容易にできて、コアプロジェクトを壊すことなく安全に作業できます。

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 ローカルテスト用にDevelopersフォルダを使うこと ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

プロジェクトの開発中に、コアプロジェクトを危険にさらすことなく自由に実験できる「サンドボックス」のようなものをチームメンバーが持つことはよくあるです。この作業が進行中でも、これらのチームメンバがプロジェクトのソース管理サーバーにアセットを配置したいと思うかもしれません。すべてのチームがデベロッパーフォルダの使用を必要とするわけではありませんが、これを使用するチームはアセットをソース管理に提出する際に共通の問題に遭遇することがよくあります。

チームメンバーが、使用準備が整っていないアセットを誤って使用することは非常に簡単なのに、一旦そのアセットが削除されると問題が発生する可能性があります。たとえば、アーティストが静的メッシュの一連の処理を反復していて、サイジングとグリッドのスナッピングが修正され続けているとします。このアセットは信じられないほどの変更や削除を受ける可能性がありますが、それがメインプロジェクトフォルダにあれば、世界の建築家はそれと知らずにレベル全体でこのアセットを使用するかもしれません。これを解決するため、チーム全員で大量の再作業を行うことになります。

これら一連のアセットがDevelopersフォルダに配置されている場合、世界の建築家はそれらを使用する理由を決して持っていないはずですし、決して問題は起こりません。コンテンツブラウザには、デベロッパーフォルダを非表示にする特定の表示オプションがあります（デフォルトでは非表示になっています）ので、通常の使用状態で誤ってデベロッパーアセットを使用することはできません。

アセットを使用できるようになると、アーティストはアセットをプロジェクト固有のフォルダに移動し、リダイレクタを修正しなければなりません。これは実質、アセットを実験段階から製品段階に「昇格」させることです。

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 すべてのMap[<sup>*</sup>](#terms-level-map) ファイルは、Mapsフォルダに配置すること ![#](https://img.shields.io/badge/lint-supported-green.svg)

Mapファイルは信じられないほど特殊で、特にサブレベルやストリーミングレベルで作業する場合は、プロジェクトごとに独自のマップ命名システムを使用するのが一般的です。特定のプロジェクトでどのようなマップ体系が整っていても、すべてのレベルは `/Content/Project/Maps` 以下に属している必要があります。

場所を説明することなしに特定の地図を開くように教えることができれば、大幅な時間の節約と一般的な「クオリティ・オブ・ライフ」の改善につながります。 `Maps/Campaign1/`や `Maps/Arenas`のように、レベルが`Maps`のサブフォルダ内にあるのは一般的ですが、ここで最も重要なのはすべてレベルが `/Content/Project/Maps` 内にあることです。

これにより、エンジニア向けのクック作業も簡単になります。ビルドプロセスのレベルを手入れすることは、そのために任意のフォルダを掘り下げなければならない場合、非常に不満がたまります。チームの地図がすべて1か所にある場合、誤ってビルド内の地図をクックしそこなうことはほとんどありません。また、QAプロセスだけでなくビルドスクリプトも簡単に作成できます。

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 クリティカルなブループリントやその他のアセットのために、 `Core` フォルダを使うこと ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

プロジェクトの動作に不可欠なアセットには `/Content/Project/Core`フォルダを使用してください。たとえば、 `GameMode`、` Character`、 `PlayerController`、` GameState`、 `PlayerState`、および関連するブループリントはここに属していなければなりません。

これは非常に明確な「これらに触れないでください」という他のチームメンバーへのメッセージになります。非エンジニアは `Core`フォルダに立ち入る理由はほとんどありません。優れたコード構造スタイルに従えば、デザイナーは、機能を公開する子クラスでゲームプレイを調整する必要があります。世界の建築家は、ベースクラスを潜在的に乱用するのでなく、指定されたフォルダでプレハブのブループリントを使用する必要があります。

(( [Adding Pickup Items](https://docs.unrealengine.com/latest/INT/Videos/PLZlv_N0_O1gbY4FN8pZuEPVC9PzQThNn1/sNueIWCKoco/)を参照))
例えば、プロジェクトのレベルにピックアップアクターを配置することが出来ると場合、ピックアップの基本動作を定義するピックアップの継承元クラスが `Core/Pickups` に存在するはずです。 Health(HP) または Ammo(弾薬) などの特殊化されたピックアップは、`/Content/Project/Placeables/Pickups/`のようなフォルダに存在するはずです。ゲームデザイナーはこのフォルダ内のピックアップを定義し調整することができますが、プロジェクト全体のピックアップを意図せず破損する可能性があるため、`Core/Pickups` に触れてはいけません。

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 `Assets`または` AssetTypes`というフォルダを作成しないこと ![#](https://img.shields.io/badge/lint-supported-green.svg)

<a name="2.6.1"></a>
#### 2.6.1 `Assets`という名前のフォルダを作成することは冗長です　 ![#](https://img.shields.io/badge/lint-supported-green.svg)

全てのアセットはアセットです。

<a name="2.6.2"></a>
#### 2.6.2 `Meshes`、` Textures`、または `Materials`という名前のフォルダを作成することは冗長です　 ![#](https://img.shields.io/badge/lint-supported-green.svg)

すべてのアセット名は、そのアセットタイプを念頭に置いて命名されます。従って、これらのフォルダは冗長な情報しか提供しません。これらのフォルダの使用は、コンテンツブラウザが提供する堅牢で使いやすいフィルタリングシステムで簡単に置き換えることができます。

 `Environment/Rocks/` の静的メッシュだけを表示したいですか？ そうなら静的メッシュフィルターをオンにするだけです。すべてのアセットが命名規則に準じてる場合は、接頭辞に関係なくアルファベット順にソートされます。静的メッシュとスケルトンメッシュの両方を表示したいですか？ 両方のフィルターをオンにするだけです。これにより、コンテンツブラウザのツリービューで2つのフォルダを `Control-Click`(複数選択) する必要がなくなります。

> これは、ほんの僅かな利点のためにアセットのフルパス名を無駄に延長することにもなります。静的メッシュの `S_` 接頭辞は2文字しかありませんが、`Meshes/`は7文字もあります。

これを守らないと、誰かが静的メッシュやテクスチャを `Materials`フォルダに置いてしまうこともありえます。

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 非常に大きなアセットのセットは、独自のフォルダレイアウトを取ります ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

これは、 [2.6](#2.6) に対してほとんど例外とみなすことができます。

膨大な量の関連ファイルを持つ特定のアセットタイプがあり、そのアセットタイプにおいて各アセットは独自の目的を持っています。最も一般的な2つは、アニメーションとオーディオのアセットです。 一つのフォルダ配下に属しているこれらのアセットが15以上あることが判明した場合、それらは一つのフォルダ直下に置く必要があります。

たとえば、複数のキャラクターを共有するアニメーションは、`Characters/Common/Animations` にあり、`Locomotion` や `Cinematic` などのサブフォルダを持つことがあります。

> これはテクスチャやマテリアルなどのアセットには適用されません。 大量の岩石がある場合、 `Rocks` フォルダは大量のテクスチャを持つのが一般的ですが、これらのテクスチャは一般的には特定の岩石にしか関連しておらず、適切に名前を付ける必要があります。 これらのテクスチャが [Material Library](#2.8) の一部であってもそれは変わりません。

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `MaterialLibrary` ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

プロジェクトでマスターマテリアル、レイヤードマテリアル、またはアセットのサブセットに属しない再利用可能なマテリアルやテクスチャを使用する場合、これらのアセットは `Content/Project/MaterialLibrary` に配置する必要があります。

このようにして、すべての「グローバル」マテリアルは生きるべき場所を持ち、簡単に見つけられます。

> これにより、プロジェクト内で「材料インスタンスのみ使用」ポリシーを課すことも非常に容易になります。すべてのアーティストとアセットがマテリアルインスタンスを使用する必要がある場合は、存在するべき正規のアセットのみがこのフォルダ内にあります。 `MaterialLibrary` 以外のフォルダ内のベースマテリアルを検索することで、これを簡単に確認できます。

`MaterialLibrary` は、純粋なマテリアルのみで構成される必要はありません。共有ユーティリティテクスチャ、マテリアル関数、およびその他この性質をもつものはここに、つまり意図した目的を負うフォルダ内に格納する必要があります。例えば、一般的なノイズテクスチャは `MaterialLibrary/Utility` に置かなければなりません。

テストやデバッグのためのマテリアルは `MaterialLibrary/Debug` の中になければなりません。これにより、出荷前にデバッグマテリアルをプロジェクトから簡単に取り除くことができ、参照エラーが表示されるかどうかで、プロダクトアセットがそれらを使用しているかどうかがはっきり明確になります。

<a name="2.9"></a>
<a name="structure-no-empty-folders"></a>
### 2.9 空っぽのフォルダはダメです ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

単純に空っぽのフォルダは在るべきでないです。それらはコンテンツブラウザを混乱させます。

もしコンテンツブラウザに空フォルダは発見及び削除不可能であるなら、以下操作を行う必要があります:
1. ソースコントロールを使用しているか確認します
1. 即座にあなたのプロジェクトで、(( [Redirector](https://docs.unrealengine.com/latest/JPN/Engine/Basics/Redirectors/index.html) ))のFixUpを選択します。
1. そのフォルダに移動して、アッセトを削除します
1. Unreal Editorを閉じます
1. ソースコントロールと同期をとります（ 例えば、PerforceでコンテンツディレクトリでのOffline作業でreconcileを実行するなど ）
1. Unreal Editorを開きます。全てが期待動作することを確認します。もしだめなら、revertして、何故うまくいかなかったかを確認して、再挑戦します
1. フォルダが消えたことを確認します
1. ソースコントロールに登録します

**[⬆ Back to Top](#table-of-contents)**


<a name="3"></a>
<a name="bp"></a>
## 3. ブループリントについて ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

このセクションでは、Blueprintクラスとその内部について説明します。 可能であれば、スタイルルールは [Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard) に準拠しています。

覚えておいてください：Blueprintではどれだけ失敗しても問題ありません。 （[KorkuVeren](http://github.com/KorkuVeren)曰く）

### セクション

> 3.1 [コンパイル(Compiling)](#bp-compiling)

> 3.2 [変数(Variables)](#bp-vars)

> 3.3 [関数(Functions)](#bp-functions) 

> 3.4 [グラフエディタ(Graphs)](#bp-graphs) 

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 コンパイル(Compiling) ![#](https://img.shields.io/badge/lint-supported-green.svg)

すべてのブループリントは、警告及びエラー無しで、コンパイルする必要があります。放置しておくと非常に恐ろしい予期しない動作へと次々につながるので、ブループリントの警告とエラーを直ちに修正するべきです。

破損したブループリントをSVN/git等に(ソースのバージョン管理システム)にコミット **しないでください**。 それらをどうしてもSVN等に保存する必要がある場合は、代わりに延期してください。

壊れたブループリントは、壊れた参照、予期しない動作、料理の失敗、頻繁で不要な再コンパイルなど、別の方法で現れる問題を引き起こす可能性があります。 壊れたブループリントはあなたのゲーム全体を破壊する力を持っています。

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 変数(Variables) ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

(( [ブループリントの変数](https://docs.unrealengine.com/latest/JPN/Engine/Blueprints/UserGuide/Variables/index.html)を参照 ))

「変数」と「プロパティ」という言葉は、同じ意味で使用できます。

#### セクション

> 3.2.1 [名前付け(Naming)](#bp-vars)

> 3.2.2 [編集可能(Editable)](#bp-vars-editable)

> 3.2.3 [分類(Categories)](#bp-vars-categories)

> 3.2.4 [アクセス(Access)](#bp-vars-access)

> 3.2.5 [高度(Advanced)](#bp-vars-advanced)

> 3.2.6 [一時的(Transient)](#bp-vars-transient)

> 3.2.7 [設定(Config)](#bp-vars-config)

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 名前付け ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 名詞 ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

すべての非ブール変数への命名は明確で、明瞭で、説明的な名詞でなければなりません。

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 PascalCase ![#](https://img.shields.io/badge/lint-supported-green.svg)

すべての非ブール変数は [PascalCase](#terms-cases) の形式にするべきです。

<a name="3.2.1.2e"></a>
###### 3.2.1.2e 例:

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3 Boopleanの接頭辞は `b`　にするべき ![#](https://img.shields.io/badge/lint-supported-green.svg)

すべてのブール値はPascalCaseで命名するべきですが、先頭に小文字の `b` を付けます。

例： `Dead`と` Evil` **ではなく**、 `bDead`と` bEvil`を使用して下さい。

UE4 Blueprint editors は、変数の使いやすい表示に `b` を含めないことを知っています。

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 ブール値の命名規則 ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1 一般かつ独立した状態の情報(General And Independent State Information) ![#](https://img.shields.io/badge/lint-supported-green.svg)

すべてのブール値は、一般的な情報を表すならば可能なときには叙述的な形容詞として命名されるべきである。 その変数を疑問として含む単語、例えば `Is`を含めないでください。 これは関数用として予約済みです。

例： `bIsDead` と `bIsHostile` **ではなく**、 `bDead`と` bHostile` を使用して下さい。

`bRunning`のような動詞を使わないでください。 動詞は状態の複雑化につながる傾向があります。

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 複合した状態(Complex States) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

複雑な状態または状態の依存を表すためにブール値を使用しないでください。 これは状態の追加と削除が複雑にして、可読性も悪くなります。 代わりに列挙体を使用してください。

例：武器について定義するときに、武器の補充かつ装備が **できない場合は**、 bReloadingやbEquippingを使用しないでください。 `EWeaponState`という名前の列挙体を定義し、代わりに` WeaponState`という名前のこの型の変数を使用してください。 これにより、武器に新しい状態を追加することがはるかに容易になります。

例： `bWalking`や` bSprinting`が必要な場合は `bRunning`を **使わないでください**。 これは、明確に定義された状態名を持つ列挙として定義する必要があります。

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 コンテキストの考慮(Considered Context) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

Blueprintのすべての変数への参照は常にそのコンテキストを持つので、すべての変数名はコンテキストと重複してはいけません。

<a name="3.2.1.5e"></a>
###### 3.2.1.5e 例:

`BP_PlayerCharacter`という名前のBlueprintクラスについて考えてみましょう。

**悪い場合**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

これらの変数はすべて重複して名前が付けられています。 これらの変数を定義しているのは `BP_PlayerCharacter`なので、変数はその変数が属する`BP_PlayerCharacter`を表しています。

**良い場合**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

((上記のように、`BP_PlayerCharacter`に属する変数であることを考慮して、シンプルに表すべきです))

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6 アトミック型名を変数名に含める _べきでない_ (Do _Not_ Include Atomic Type Names) ![#](https://img.shields.io/badge/lint-supported-green.svg)

Atomicまたはプリミティブ変数は、ブール値、整数、浮動小数点数、および列挙型など、最も単純な形式のデータを表す変数です。

ブループリントで作業する場合、StringやVectorはスタイルの観点からアトミック的であるとみなされますが、正確にはアトミックではありません。

> Vector(ベクトル)は3つの浮動小数点で構成されますが、Vectorは回転子と同じように全体として操作することができます。

> Text変数をアトミックとはみなしません、なぜなら密かにローカライゼーション用機能を隠しています。文字列のアトミックタイプは `Text`ではなく` String`です。

Atomic変数は、それら変数名に型名を含むべきではありません。

例： `Score`、` Kills`、`Description` を使用します。` ScoreFloat`、 `FloatKills`、` DescriptionString` **ではなく** 

このルールの唯一の例外は、変数が変数の型を持たない名前を使うのが読みにくい場合に、変数が '数えられる何か' を表していることです。

例：柵(フェンス)ジェネレータは、X個のポストを生成する必要がある場合、`Posts`という変数名は`Post`という変数型の配列として認識される可能性がありますので、`Posts`代わにに`NumPosts`や` PostsCount`の命名の変数に、生成個数のXを記録します。 

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 非アトミック型名は変数名に含めるべき (Do Include Non-Atomic Type Names) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

非Atomicまたは複合変数は、データをアトミック変数の集合として表す変数です。 `Text`や` Name`のような隠れた振る舞いを持つ構造体、クラス、インタフェース、プリミティブはすべてこのルールの対象となります。

> アトミック変数型の配列は変数のリストですが、配列は変数型の '原子性(atomicness)' を変更しません。

これらの変数名は、コンテキストを考慮しつつ型名を含めるべきです。

またあるクラスが複雑な変数インスタンスを包含している場合、つまり `BP_PlayerCharacter`が` BP_Hat`を所有しているなら名前の変更無しに変数型として格納するべきです。

例：`Hat`、` Flag`、 `Ability` を使用します。  `MyHat`、`MyFlag`、` PlayerAbility` **ではなく** 

またあるクラスが複雑な変数インスタンスを表すものを包含していない場合は、変数型と一緒に名詞を使用するべきです。

例： `BP_Turret`(樽)が` BP_PlayerCharacter`(プレイヤー)を対象とする機能を有しているなら、 `BP_Turret`のコンテキストに` TargetPlayer`の複雑な変数インスタンスを所有しないように、明確に参照(リファレンス)を保存するべきです。


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 ((Type:))配列(Arrays) ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

配列は上記と同じ命名規則に従いますが、複数名詞として命名するべきです。

例： `TargetList`、` HatArray`、 `EnemyPlayerArray` **ではなく** `Target`、` Hats`、 `EnemyPlayers` を使用します。

<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 ((option:))Editable Variables((パブリックで編集可能のon/off)) ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

ブループリントの動作を設定するために値を変更するのに安全なすべての変数は、`編集可能 (Editable)` としてマークするべきです。

逆に、安全に変更出来ないまたはデザイナーに公開されるべきでないすべての変数は、 `スポーン時に公開 (Expose On Spawn)` としてマークするべきエンジニアリング上の理由がない限り、編集可能にしてはいけません。

変数を `編集可能` として勝手にマークしないでください。

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 ((option:))ツールヒント(Tooltips) ![#](https://img.shields.io/badge/lint-supported-green.svg)

編集可能とマークされた変数を含むすべての `編集可能`変数は、`スポーン時に公開`としてマークすることができるので、この値の変更がブループリントの動作にどのように影響するかを説明する `ツールヒント (Tooltip)` フィールドに記述するべきです。

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
<!-- https://forums.unrealengine.com/showthread.php?65227-Float-Variable-With-Slider-Range-From-C -->
##### 3.2.2.2 ((option:))スライダと値の範囲(Slider And Value Ranges) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

すべての `Editable`変数は、その変数に設定されては _ならない_ 値が存在する場合、スライダと値の範囲を使用するべきです。

例：フェンスの支柱を生成するブループリントには、編集可能な変数 `PostsCount` がある場合、-1の値を設定できても意味が無いでしょう。 範囲フィールドを使用して0を最小値として設定します。

編集可能な変数がコンストラクションスクリプト(Construction Script)で使用されている場合は、誤ってエディタをクラッシュさせるような大きな値を設定出来ないように、適切なスライダ範囲が定義するべきです。

値範囲は、値の境界がわかっている場合にのみ定義する必要があります。 スライダ範囲は偶発的な多数の入力を防ぎますが、未定義の値範囲を使用するとスライダ範囲外の値を指定することができます。この値は「危険」とみなされますが有効です。

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 カテゴリ(Categories) ![#](https://img.shields.io/badge/lint-supported-green.svg)

クラスの変数が少ない場合、カテゴリの使用は必須ではありません。

クラスの変数が適度な量（5〜10）の場合、すべての `編集可能 (Editable)`変数にはデフォルト以外のカテゴリが割り当てられます。一般的に割り当てるカテゴリは `Config`です。

クラスの変数が大量の場合、すべての `編集可能` 変数は、`Config`カテゴリを基本カテゴリとして使用してサブカテゴリに分類する必要があります。 編集不可能な変数は、その使用法を説明する記述的なカテゴリに分類されるべきです。

> パイプ文字 `|`を使ってサブカテゴリを定義することができます。すなわち `Config | Animations`

例：武器クラスの変数設定は以下のように構成されるかも:

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
#### 3.2.4 変数のアクセスレベル(Variable Access Level) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

C++では、変数にはアクセスレベルの概念があります。 Publicは、クラス外のコードが変数にアクセスできることを意味します。 Protectedは、クラスおよびすべての子クラスだけがこの変数に内部的にアクセスできることを意味します。 Privateはこのクラスのみを意味し、この変数には子クラスはアクセスできません。

ブループリントには現在、Protectedのアクセスの制御の概念が定義されていません。

`編集可能 (Editable)` 変数をPublic(公開)変数として扱います。 編集不可能な変数をProtected(保護)変数として扱います。

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 非公開変数(Private Variables) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

変数が定義したクラス内でしか使用されず絶対に子クラスで無い場合を除き、変数をプライベートとしてマークしないでください。 変数が `protected`とマークされるまで、子クラスの使用を制限したいことが絶対に分かっているときは、privateであることを保持してください。

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
<!-- https://wiki.unrealengine.com/UPROPERTY -->
#### 3.2.5 ((option:))詳細表示(Advanced Display) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

変数を `編集可能` であるが、頻繁には値を変更しない場合は、それを `Advanced Display` をマークするべきです。 これにより、拡張表示矢印をクリックしない限り、変数が非表示になります。

`Advanced Display`オプションを検索するには、詳細表示された変数として変数の詳細一覧に表示されます。

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 ((option:))一時変数(Transient Variables) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

一時変数とは、値を保存して読み込む必要がなく、ゼロまたはゼロの初期値を持つ変数です。 これは、実行時まで値がわからない他のオブジェクトやアクタへの参照に役立ちます。これはエディタによってそのリファレンスが保存されることを防ぎ、Blueprintクラスの保存と読み込みが高速化されます。

このため、全ての一時変数は常にゼロまたはnullとして初期化しておく必要があります。 でないとエラーをデバッグするのが難しくなります。

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 ((option:))構成変数(Config Variables) ![#](https://img.shields.io/badge/lint-supported-green.svg)

`Config Variable`フラグは使わないでください。 これにより、設計者は ブループリント の動作を制御することが難しくなります。 構成変数は、まれに変更された変数に対してのみC++で使用する必要があります。 それらを `Advanced Advanced Display` 変数と考えてください。

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 関数、イベント、およびイベントディスパッチャ(Functions, Events, and Event Dispatchers) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

このセクションでは、関数、イベント、およびイベントディスパッチャの作成方法について説明します。特記事項がない限り、関数に適用されるものはすべてイベントにも適用されます。

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 関数の名前付け ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

関数、イベント、イベントディスパッチャーの命名は非常に重要です。名前だけを基に、機能についてある程度の予想がつくようになります。例えば：

* それは純粋関数か？
* それは状態情報を取得してるか？
* それはハンドラか？
* それはRPCか？
* その目的は何か？

関数の名前が適切であれば、こういった質問にすべて答えることができます。

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 すべての関数は動詞であるべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

すべての関数とイベントは、情報の取得、データの計算、または何かを爆発させるなど、何らかのアクションを実行します。したがって、すべての関数はすべて動詞で始まる必要があります。それらは現時点で可能な限り語られるべきです。それらはまた、関数等が何をしているかについていくつかのコンテキストを持つべきです。

`OnRep` 関数、イベントハンドラ、およびイベントディスパッチャは、このルールの例外です。

良い例：

* `Fire` - Character/Weaponクラスの場合は良い例です、それの持っているコンテキストに即しています。Barrel/Grass/及び他のあいまいなクラスであれば悪い例です。
* `Jump` - Characterクラス中であればい例です、他の場合はコンテキストが必要です。
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" は動詞](http://writingexplained.org/is-is-a-verb)

悪い例：

* `Dead` - 死んでいる？これから死ぬのか？
* `Rock`
* `ProcessData` - あいまいで、これらの言葉は何も意味しません。
* `PlayerState` - 名詞はあいまいです。
* `Color` - コンテキストのない動詞、あいまいな名詞。

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
<!-- https://docs.unrealengine.com/latest/JPN/Resources/ContentExamples/Networking/1_4/index.html -->
#### 3.3.1.2  ((option:)) RepNotify関数プロパティは常に `OnRep_Variable` の形式であるべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

通知変数で複製されるすべての関数は、 `OnRep_Variable` の形式でなければなりません。これはBlueprintエディタによって強制されます。ただし、C++ の `OnRep` 関数を記述している場合、それをBlueprintsに公開する際にはこの規則に従ってください。

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3  Boolを返す情報関数は質問形式にするべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

状態を変えず、どんなオブジェクトも更新せず、単に情報、状態、またはboolのyes/noを取得するための関数を書くときには質問形式にするべきです。同時に [動詞規則](#bp-funcs-naming-verbs) にも従うべきです。

これは質問形式でなければ、その関数がアクションを実行し、そのアクションが成功したかどうかを返すと仮定してよいのと同様に非常に重要です。

良い例：

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" は動詞](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" は "be"の過去形](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) '前のフレーム' または '前の状態' を参照するとき "was" を使用.
* `CanReload` - ["Can" は動詞](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

悪い例：

* `Fire` - 燃えている？ 発砲するか？ 燃やすのか？
* `OnFire` - 発射のイベントディスパッチャと混同することがあります。
* `Dead` - 死んでいる？これから死ぬのか？
* `Visibility` - 視認出来る？ 可視化する？ 飛行条件の説明？

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 イベントハンドラとディスパッチャは `On` で始まるべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

イベントハンドラや、イベントディスパッチなどの関数は、`On` で始まるべきで、後は [動詞規則](#bp-funcs-naming-verbs) に従ってください。 ただし、過去刑であることがうまく読み取れる場合は、動詞を末尾に移動した方がよいかもしれません。

単語 `On` の[連結語句](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation)は、動詞規則に従うことが免除されます。

`Handle` を使用することは許されません。'Unreal' では `Handle` の代わりに` On` を使用しますが、他のフレームワークでは `On`の代わりに` Handle` を使う方がよいかもしれません。

良い例：

* `OnDeath` - ゲームの一般的な連結語句
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

悪い例：

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 リモートプロシージャコールにはターゲットが前置されるべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

RPCを作成する場合は、いつでも `Server`、` Client`、または `Multicast`の接頭辞が付いていなければなりません。一切の例外なくです。

接頭辞の後に、関数命名に関する他のすべての規則に従ってください。

良い例：

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

悪い例：

* `FireWeapon` - 何らかの種類のRPCを示すものではありません。
* `ServerClientBroadcast` - 混乱します。
* `AllNotifyDeath` - ` Multicast` を使用し、決して `All` を使用しないでください。
* `ClientWeapon` - 動詞ではなく、あいまいです。


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
<!-- https://answers.unrealengine.com/questions/139959/how-can-i-create-return-node.html -->
#### 3.3.2 すべての関数にReturnノードが必須 ![#](https://img.shields.io/badge/lint-supported-green.svg)

すべての関数にReturnノードは必要です。例外はありません。

Returnノードは、関数の実行が終了したことを明示します。Blueprintが `Sequence`、` ForLoopWithBreak`、および逆向きのrerouteノードで満たされる世界では、可読性、メンテナンス、およびデバッグの容易さのために明示的な実行フローが重要です。

Blueprintコンパイラーは実行フローを追うことができ、Returnノードを使用すれば、ハンドルされないReturnまたは不良なフローがコードのブランチにあるかどうかを警告します。

プログラマがfor節を追加したり、forループが完了した後にロジックを追加してループの反復が早期に返ったりするような状況では、コードフローに偶発的なエラーが生じることがあります。 Blueprintコンパイラの警告は、これらの問題のすべてを直ちに警告します。


<a name="3.3.3"></a> 
<a name="bp-graphs-funcs-node-limit"></a> 
#### 3.3.3 関数のノード数は50未満に抑えるべき ![#](https://img.shields.io/badge/lint-supported-green.svg)

まず関数は50以上のノードを持つべきでありません。そのような大きな関数は、可読性と保守性のためさらに小さな関数に機能分割するべきです。

以下に記載のノード達は、関数の複雑性を増大させないと思いますので、カウントしません：

* Comment 
* Route 
* Cast 
* Getting a Variable 
* Breaking a Struct 
* Function Entry 
* Self 

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 全てのPublic関数には説明文	を記載するべき ![#](https://img.shields.io/badge/lint-supported-green.svg)

本ルールは、一般公開されている又はマーケットプレイスのblueprintなど多数に適用される。そのため本ルールが守られていると、これの使用者はblueprint APIをより簡単に説明に案内されて使用することができます。

単純に、アクセス指定にがPublicを設定された関数は、その操作等について説明を十分に記載するべきです。

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 ((???)) すべてのカスタム静的プラグイン `BlueprintCallable`関数はプラグイン名でカテゴライズ(分類)されるべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

もしあなたのプロジェクトに `static` で `BlueprintCallable` の定義された関数がプラグイン等が含まれている場合、それらのカテゴリは、プラグイン名またはプラグイン名のサブセットカテゴリに設定する必要べきです。

例として、 `Zed Camera Interface` や `Zed Camera Interface | Image Capturing`。

(( [ゲームプレイ要素をブループリントに公開する](https://docs.unrealengine.com/latest/JPN/Engine/Blueprints/TechnicalGuide/ExtendingBlueprints/index.html) ))

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprintグラフ (Blueprint Graphs) ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

このセクションでは、すべてのBlueprintグラフに適用される事項について説明します。

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 スパゲティをなくせ ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

ワイヤーの始点と終点が明確になるように配置しましょう。グラフを理解するためにわざわざ頭の中でワイヤーをほどく必要はありません。以下のセクションでは、スパゲティを減らすことに紙面の多くを割いています。

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
<!-- https://answers.unrealengine.com/questions/323566/unreal-engin-why-u-make-me-so-angry.html -->
#### 3.4.2 ノードではなくワイヤーを整列すべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

いつでもノードではなくワイヤーを整列させてください。ノードのサイズとピン位置を常に制御することはできませんが、ノードの位置を制御しすることとそれによりワイヤーを制御することはいつでもできます。真っ直ぐなワイヤーのラインは、フローをわかりやすくします。凸凹に波打つワイヤーのラインはひどくわかりにくいです。BPノードを選択してStraigten Connectionsコマンドを使用することにより、ワイヤを真っ直ぐにすることができます。Hotkey: Q

良い例：ノードの上部は、白い実行ワイヤーラインを真っ直ぐに維持するためにずらしてあります。
![Aligned By Wires](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-good.png "ワイヤによって整列")

悪い例：ノードの上端が一直線に並んでいますが、白い実行ワイヤーラインが凸凹に波打っています。
![Bad](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-bad.png "凸凹に波打つ")

許容可能な例：特定のノードは、アラインメントツールの使い方にかかわらずうまく機能しないかもしれません。このような状況では、ノードをより近くに持っていくことで、凸凹に波打つのを最小限に抑えてください。
![Acceptable](https://github.com/allar/ue4-style-guide/raw/master/images/bp-graphs-align-wires-acceptable.png "受け入れ可能(Acceptable)")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 白い実行ワイヤーを最優先にするべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

直線状の白い実行ワイヤーを真っ直ぐにするか、なんらかのデータワイヤーを真っ直ぐにするかが選択肢として与えられたら、いつでも白い実行ワイヤーを真っ直ぐにするべきです。

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 グラフには分かり易いコメントを書くべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

ノードブロックは、大まかな振る舞いについて記載したコメントノードで、それらを囲う必要があります。個々のノードを読み易くと理解しやすいくするため、すべての関数により良い命名を行う必要があり、目的を達するためのノードグループ群には、それの目的をコメントブロックとして記述するべきです。もし関数が多くのノードブロックをもたず、ノードが関数の目的を直接提供していることが明確であるなら、関数名とその説明で十分で、コメントは不要です。

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 グラフの適切な場所でキャストエラーを処理するべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

もし関数またはイベントのキャストが常に成功する前提の場合、キャストが失敗した場合にそのロジックの失敗を適切に報告するべきです。これは他者に何が起こったか、つまり「動作すると想定する」ことが失敗したことを知らせます。キャストされた参照が、キャストに失敗する可能性があることが分かっている場合、関数はキャストエラーの後でも正常な回復を試みるべきです。

これは、全てのキャストノードがそのエラー処理を行う必要があることを意味しません。多くの場合、特に衝突のような場合では、キャストエラーで実行フローが粛々とに終了されるでしょう。

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 グラフにはぶら下がり(Dangling)/緩み(Loose)/非接続ノード(Dead Nodes)は保持させるべきでない ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

全てのBlueprintグラフの、全てのノードに目的が必須です。目的が無い、または実行されない周囲にぶら下がったBlueprintノードを残すべきないです。

**[⬆ Back to Top](#table-of-contents)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. 静的メッシュについて ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

このセクションではStaticMeshアセット及びその詳細について説明を行います。

### Sections

> 4.1 [UVs](#s-uvs)

> 4.2 [LODs](#s-lods)

> 4.3 [モジュールのSocketlessはスナップされるべき](#s-modular-snapping)

> 4.4 [衝突判定(Collision)を持たなければならない](#s-collision)

> 4.5 [スケール補正(Correct Scale)](#s-scaled)

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs ![#](https://img.shields.io/badge/lint-supported-green.svg)

もしLinterが不正UVをレポート出力していて、それで原因を追跡することが出来ないなら、プロジェクトの `Saved/Logs` フォルダにある結果の `.log` ファイルを開いて、失敗した理由を正確に調べてください。私はこれらのメッセージをLintのレポートに将来的に含めようと思っています。

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 全てのメッシュはUVを持たなければならない ![#](https://img.shields.io/badge/lint-supported-green.svg)

とても単純です。どのように使用するにしても、全てのメッシュはUVを持っていなければならない。

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 全てのメッシュのUVは、Lightmapsにも用いるため重ねてはいけない ![#](https://img.shields.io/badge/lint-supported-green.svg)

とても単純です。どのように使用するにしても、全てのメッシュは、重複しない有効なUVを持つべきです。

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LOD(Level of Details)は確りと設定するべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)
(( [LOD の作成と使用](https://docs.unrealengine.com/latest/JPN/Engine/Content/Types/StaticMeshes/HowTo/LODs/index.html) ))

プロジェクトごとの基本的な主観チェックですが、原則として、近距離から遠距離で表示されるメッシュには適切なLODを設定するべきです。

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 ((??))モジュールのSocketlessアセットは、グリッドに綺麗にスナップされるべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

アセットごとの基本的な主観チェックですが、モジュールのソケットレスアセットは、プロジェクトのグリッド設定に基づいてきれいにスナップするべきです。

2の累乗のグリッドか、または10単位のグリッドにスナップするかは、プロジェクトしだいですが、しかしmarketplace用のモジュールのソケットレスアセットを作成する場合、Epic社の要件は、グリッドが10単位以上に設定されている場合に、きれいにスナップすることです。

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 全てのメッシュはコリジョン(衝突判定)を持たなければならない ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

アセットがレベル中でコリジョンのために使用されるかどうかに関わらず、全てのメッシュには適切なコリジョンが設定されているべきです。これは境界計算やオクルージョン、ライティングなどの使用の際にUE4エンジンを援助します。コリジョンはまたアッセトに対して正格であるべきです。

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 全てのメッシュは正しくスケーリングするべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

プロジェクトごとの基本的な主観的なチェックですが、すべてのアセットはプロジェクトに正しくスケーリングされている必要があります。レベルデザイナーまたはブループリント作者は、エディターで確認するためにメッシュのスケールを調整する必要はありません。((?))エンジンのスケーリングメッシュは、スケール補正ではなく、スケール上書きとして扱うべきです。

**[⬆ Back to Top](#table-of-contents)**


<a name="5"></a>
<a name="Particle Systems"></a>
<a name="ps"></a>
## 5. パーティクルシステムについて ![#](https://img.shields.io/badge/lint-supported-green.svg)

このセクションではParticle Systemアセット及びその詳細について説明を行います。

### Sections

> 5.1 [エミット命名](#ps-naming)

<a name="5.1"></a>
<a name="ps-emitter-naming"></a>
### 5.1 エミット命名 ![#](https://img.shields.io/badge/lint-supported-green.svg)

パーティクルシステムの全ててのエミッタには、説明的な名前を付けて、デフォルトの "パーティクルエミッタ" にするべきでないです。

**[⬆ Back to Top](#table-of-contents)**


<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels/Mapsについて ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

[重要用語のLevels/Mapsを参照](#terms-level-map) "levels" 対 "maps" に関して

このセクションではLevelアセット及びその詳細について説明を行います。

### Sections

> 6.1 [エラーや警告を残さないこと](#levels-no-errors-or-warnings)

> 6.2 [ライティングビルドするべき](#levels-lighting-should-be-built)

> 6.3 [プレイヤーにＺファイティングを見せるな](#evels-no-visible-z-fighting)

> 6.4 [マーケットプレイスの特殊ルール](#evels-levels-mp-rules)

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 エラーや警告を残さないこと ![#](https://img.shields.io/badge/lint-partial_support-yellow.svg)

全てのレベルは、エラーまたは警告がゼロ個でロードされるべきです。 Levelにエラーや警告が含まれている場合は、直ちに修正してカスケード問題を防ぐ必要があります。

コンソールより "map check" コマンドによって、エディタで開いているレベルのマップをチェックすることが出来ます。

注意：Linterは現在のエディタのチェックよりも厳密であり、((?)) エディタ自身で解決するロードエラーをキャッチします。

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 ライティングビルドするべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

開発中には、レベルで時折ライティングビルドをしていなかったりしますが、問題ないです。 けれどもそれらが配布物、テスト/内部/出荷(shipping)ビルドやその他のビルド、の場合には常にライティングビルドを実施するべきです。

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 プレイヤーにＺファイティング(Fighting) を見せるな ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

レベルは、プレイヤーに見える全ての領域で[z-fighting](https://en.wikipedia.org/wiki/Z-fighting)を無くすべきです。

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 マーケットプレイスの特殊ルール ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

もしプロジェクトをUE4マーケットプレイスで販売する場合、以下のルールを守らなけれなりません。

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
### 6.4.1 概要レベル ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

もしあなたのプロジェクトに、視覚化される、またはデモするべきアセットが含まれている場合は、プロジェクトに "Overview" という名前のマップの作成が必須です。

この概要(Overview)マップが、もしアセットを視覚化している[Epic's guidelines](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps)に従って設定されるべきです。

例えば、`InteractionComponent_Overview`。

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
### 6.4.2 デモレベル ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

もしプロジェクトにデモする必要があるアセットが含まれている場合や、何らかのチュートリアルが必要な場合は、プロジェクト内に "Demo" という名前のマップの作成が必須です。 このレベルには、プロジェクト内の使用方法を示す形式のドキュメントも含まれている必要があります。 これを行う方法ついては、EpicのContent Examplesプロジェクトなどが良い例です。。

あなたのプロジェクトが、アートパックではなくゲームプレイのメカニズムや他のシステムである場合、これは "Overview" マップと同じようにできます。

例えば `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Back to Top](#table-of-contents)**


<a name="7"></a>
<a name="textures"></a>
## 7. テクスチャ ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

このセクションではParticle Textureアセット及びその詳細について説明を行います。

### Sections

> 7.1 [寸法は2の累乗にすべき](#textures-dimension)

> 7.2 [テクスチャ密度は統一するべき](#textures-dimension)

> 7.3 [テクスチャは8192より大きくするべきではない](#textures-max-size)

> 7.4 [テクスチャは正しくグループ化するべき](#textures-textures-group)

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 寸法は2の累乗にすべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

UIテクスチャを除く全てのテクスチャは、次元数が2の累乗でなければなりません。またテクスチャは正方形である必要はありません。

例えば, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 テクスチャ密度(DPI)は統一するべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

すべてのテクスチャは、それらの標準的なユースケースに適したサイズにするべきです。 適切なテクスチャ密度はプロジェクトごとに異なりますが、そのプロジェクト内の全てのテクスチャは一貫した密度を持つべきです。

例えば、もしプロジェクトのテクスチャ密度が1単位あたり8ピクセルの場合、100x100単位の立方体に適用されるテクスチャは、プロジェクトのテクスチャ密度に最も近いのは2の累乗である1024x1024である必要があります。

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 テクスチャは8K(8192)より大きくするべきではない ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

非常に明示的な理由がない限り、テクスチャのサイズは8192を超えてはいけません。 多くの場合、これを超えるサイズのテスクチャの使用は、単にリソースの無駄にすぎません。

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 テクスチャは正しくグループ化するべき ![#](https://img.shields.io/badge/lint-unsupported-red.svg)

全てのテクスチャは、LODに使用されるTexture Groupプロパティを持っています。そしてそれは使用に基づいて正しく設定するべきです。 例えば、全てのUIテクスチャはUIテクスチャグループに属すべきです。

**[⬆ Back to Top](#table-of-contents)**


## Contributors

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Back to Top](#table-of-contents)**


## Amendments

このガイドをフォークしてチームのスタイルガイドに合わせてルールを変更することを推奨します。 ここより以下にスタイルガイドの修正案を上げられてはどうでしょうか。こうすることによりマージの際にコンフリクトすることなく、スタイルガイドを定期的に更新することが出来ます。

# };
