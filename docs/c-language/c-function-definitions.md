---
title: Definice funkcí jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
ms.openlocfilehash: 5cf56375df417ac68b3e03d00f2bd7770ee571e8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857135"
---
# <a name="c-function-definitions"></a>Definice funkcí jazyka C

Definice funkce určuje název funkce, typy a počet parametrů, které očekává přijmout, a návratový typ. Definice funkce zahrnuje také tělo funkce s deklaracemi jejích místních proměnných a příkazy, které určují, co funkce dělá.

## <a name="syntax"></a>Syntaxe

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace External* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*externí deklarace*:/\* povolena pouze v externím oboru (soubor) \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *– definice funkce*<br/>
*deklarace* &nbsp;&nbsp;&nbsp;&nbsp;

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*– atribut<sub>opt</sub> *-SEQ* *deklarátor* *deklarace-list*<sub></sub> <sub>opt –</sub> *složený* příkaz

atribut /\* *– SEQ* je specifický pro Microsoft \*/

Parametry prototypu jsou:

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*třídy úložiště* -specifikátory *deklarace specifikátor-* <sub></sub> specifikátory <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory*<sub></sub> *specifikátoru typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory*<sub></sub> *kvalifikátoru typu* -deklarace

*seznam deklarací*:<br/>
*deklarace* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;*deklarace* &nbsp;*deklarace seznamu*

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatelem*<sub>opt</sub> *Direct-deklarátor*

*Direct-deklarátor*:/\* / funkce deklarátor \*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam parametrů typu* **)**  / \* deklarátor nový styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam identifikátorů*<sub>optimalizované</sub> **)**  / \* Obsolete – vizuální styl deklarátor \*/

Seznam parametrů v definici používá tuto syntaxi:

*parametr-Type-list*:/\* \*seznamu parametrů /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* **,...**

*seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,** *deklarace parametru*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;*specifikátory deklarace* &nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *abstract-deklarátor*<sub>opt</sub>

Seznam parametrů v definici funkce starého stylu používá tuto syntaxi:

*seznam identifikátorů*:/\* používá se v definicích a deklaracích funkcí zastaralých stylů \*/<br/>
*identifikátor* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam identifikátorů* **,** *identifikátor*

Syntaxe pro tělo funkce je:

*složený příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *Declaration-list*<sub>opt</sub> *Statement-list*<sub>opt</sub> **}**

Jediný specifikátory třídy úložiště, které mohou upravit deklaraci funkce, jsou **extern** a **static**. **Extern** specifikátor znamená, že na funkci lze odkazovat z jiných souborů; To znamená, že název funkce je exportován do linkeru. **Statický** specifikátor znamená, že funkci nelze odkazovat z jiných souborů; To znamená, že název není exportován linkerem. Pokud se v definici funkce nezobrazí žádná třída úložiště, předpokládá se **extern** . V každém případě je funkce vždy viditelná z bodu definice na konec souboru.

Volitelné *specifikátory deklarace* a povinné *deklarátor* společně určují návratový typ a název funkce. *Deklarátor* je kombinace identifikátoru, který název funkce a závorky následuje po názvu funkce. Nepovinný neterminálový *atribut-seq* je funkce specifická pro společnost Microsoft, která je definována v [atributech funkce](../c-language/function-attributes.md).

*Přímý parametr-deklarátor* (v syntaxi *deklarátor* ) určuje název funkce, která je definována, a identifikátory jeho parametrů. Pokud *Direct-deklarátor* zahrnuje *seznam parametrů-Type-* , seznam určuje typy všech parametrů. Taková deklarátor také slouží jako prototyp funkce pro pozdější volání funkce.

*Deklarace* v rámci definice funkce nemůže obsahovat *specifikátor třídy úložiště* , *která je jiná* než **registr**. *Specifikátor typu* v syntaxi *specifikátoru deklarace* lze vynechat pouze v případě, že je třída úložiště **registru** zadána pro hodnotu typu **int** .

*Složený příkaz* je tělo funkce obsahující deklarace lokální proměnné, odkazy na externě deklarované položky a příkazy.

Oddíly [atributů funkce](../c-language/function-attributes.md), [třídy úložiště](../c-language/storage-class.md), [návratový typ](../c-language/return-type.md), [parametry](../c-language/parameters.md)a [tělo funkce](../c-language/function-body.md) popisují podrobně komponenty definice funkce.

## <a name="see-also"></a>Viz také:

[Funkce](../c-language/functions-c.md)
