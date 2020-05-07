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

*jednotka překladu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Externí deklarace* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*externí deklarace* *jednotky překladu*

*externí deklarace*:/\* povoleno pouze v externím (souboru) oboru\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*definice funkce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*změny*

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory*<sub>opt</sub> *atribut – seq*<sub>opt</sub> *deklarátor* *deklarace-list*<sub>opt</sub> – *složený* příkaz

/\**atribut – seq* je specifický pro společnost Microsoft\*/

Parametry prototypu jsou:

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru třídy úložiště* – *specifikátory*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru typu* *– Povolit specifikátory*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ-specifikátor deklarace kvalifikátoru* *– specifikátory*<sub>opt</sub>

*seznam deklarací*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*změny*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *seznamu deklarací* *declaration*

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*Direct-deklarátor*:/\* A – funkce deklarátor\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***(***parametr-Type-list***)**  / \* – nový styl deklarátor      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***(opt***-list*<sub>opt</sub> **)**  / \* zastaralý styl deklarátor    \*/

Seznam parametrů v definici používá tuto syntaxi:

*seznam parametrů-typu*:/\* seznam parametrů\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* **,...**

*seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* **,**  *parametr-Declaration*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory* *deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace-specifikátory* *abstract-deklarátor*<sub>opt</sub>

Seznam parametrů v definici funkce starého stylu používá tuto syntaxi:

*seznam identifikátorů*:/\* používá se v definicích a deklaracích funkcí zastaralých stylů.\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam identifikátorů* **,**  *identifikátor*

Syntaxe pro tělo funkce je:

*složený příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklarace-seznam*příkazů<sub>opt</sub> *-list*<sub>opt</sub> **}**

Jediný specifikátory třídy úložiště, které mohou upravit deklaraci funkce, jsou **extern** a **static**. **Extern** specifikátor znamená, že na funkci lze odkazovat z jiných souborů; To znamená, že název funkce je exportován do linkeru. **Statický** specifikátor znamená, že funkci nelze odkazovat z jiných souborů; To znamená, že název není exportován linkerem. Pokud se v definici funkce nezobrazí žádná třída úložiště, předpokládá se **extern** . V každém případě je funkce vždy viditelná z bodu definice na konec souboru.

Volitelné *specifikátory deklarace* a povinné *deklarátor* společně určují návratový typ a název funkce. *Deklarátor* je kombinace identifikátoru, který název funkce a závorky následuje po názvu funkce. Nepovinný neterminálový *atribut-seq* je funkce specifická pro společnost Microsoft, která je definována v [atributech funkce](../c-language/function-attributes.md).

*Přímý parametr-deklarátor* (v syntaxi *deklarátor* ) určuje název funkce, která je definována, a identifikátory jeho parametrů. Pokud *Direct-deklarátor* zahrnuje *seznam parametrů-Type-*, seznam určuje typy všech parametrů. Taková deklarátor také slouží jako prototyp funkce pro pozdější volání funkce.

*Deklarace* v rámci definice funkce nemůže obsahovat *specifikátor třídy úložiště* , *která je jiná* než **registr**. *Specifikátor typu* v syntaxi *specifikátoru deklarace* lze vynechat pouze v případě, že je třída úložiště **registru** zadána pro hodnotu typu **int** .

*Složený příkaz* je tělo funkce obsahující deklarace lokální proměnné, odkazy na externě deklarované položky a příkazy.

Oddíly [atributů funkce](../c-language/function-attributes.md), [třídy úložiště](../c-language/storage-class.md), [návratový typ](../c-language/return-type.md), [parametry](../c-language/parameters.md)a [tělo funkce](../c-language/function-body.md) popisují podrobně komponenty definice funkce.

## <a name="see-also"></a>Viz také

[Functions](../c-language/functions-c.md)
