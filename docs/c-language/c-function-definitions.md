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
ms.openlocfilehash: 61662caf28fad2f961a580cf280799711a6909bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325647"
---
# <a name="c-function-definitions"></a>Definice funkcí jazyka C

Definice funkce určuje název funkce, typy a počet parametrů, které se očekává, že pro příjem a její typ vrácené hodnoty. Definice funkce také obsahuje tělo funkce s deklarací své místní proměnné a příkazy, které určují, co funkce dělá.

## <a name="syntax"></a>Syntaxe

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*externí deklarace*: /\* povolený jenom v oboru externí (soubor) \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*definice funkce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace*

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*<sub>optimalizované</sub> *sekvence atributů*<sub>optimalizované</sub> *deklarátor* *seznam deklarací*  <sub>optimalizované</sub> *compound-statement*

/\* *sekvence atributů* je specifické pro Microsoft \*/

Prototyp parametry jsou:

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specifikátory deklarace*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>

*seznam deklarací*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam deklarací* *deklarace*

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*přímé declarator*: /\* deklarátorem funkce \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam parametrů typu* **)**  / \* deklarátor nový styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam identifikátorů*<sub>optimalizované</sub> **)**  / \* Obsolete – vizuální styl deklarátor \*/

Seznam parametrů v definici používá tuto syntaxi:

*Seznam parametrů typu*: /\* seznam parametrů \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,...**

*Seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,** *deklarace parametru*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *deklarátorů*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *abstraktní deklarátor*<sub>optimalizované</sub>

Seznam parametrů v definici funkce starého typu používá tuto syntaxi:

*Seznam identifikátorů*: /\* používané funkce zastaralé definice a deklarace \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam identifikátorů* **,** *identifikátor*

Syntaxe pro tělo funkce je:

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *seznam deklarací*<sub>optimalizované</sub> *seznamu příkazů*<sub>optimalizované</sub> **}**

Jsou pouze specifikátory třídy úložiště, které můžete upravit deklaraci funkce **extern** a **statické**. **Extern** specifikátor znamená, že funkci můžete odkazovat z jiných souborů; to znamená, název funkce se exportují do propojovacího programu. **Statické** specifikátor znamená, že funkce se nedá odkazovat z jiných souborů; to znamená, že název neexportoval linkerem. Pokud žádnou třídu úložiště se zobrazí v definici funkce **extern** se předpokládá, že. V každém případě je vždy viditelná z místa definice na konec souboru.

Volitelný *specifikátory deklarace* a povinná *deklarátor* definujte návratový typ funkce a název. *Deklarátor* je kombinací identifikátoru s názvem funkce a závorek za název funkce. Volitelný *sekvence atributů* nonterminal specifické pro společnost Microsoft je funkce definované v [atributy funkce](../c-language/function-attributes.md).

*Direct-declarator* (v *deklarátor* syntaxi) určuje název funkce je definována a identifikátory ze svých parametrů. Pokud *direct-declarator* zahrnuje *seznam parametrů typu*, seznamu určuje typy všech parametrů. Takové deklarátorem slouží taky jako prototyp funkce pro pozdější volání funkce.

A *deklarace* v *seznam deklarací* ve funkci nemůže obsahovat definice *storage-class-specifier* jiné než **zaregistrovat**. *Specifikátor typu* v *specifikátory deklarace* syntaxe lze vynechat jenom v případě **zaregistrovat** třídu úložiště je určená pro hodnotu **int** typu.

*Compound-statement* je tělo funkce obsahující deklarace místních proměnných, odkazy na externě deklarovaná položky a příkazy.

V částech [atributy funkce](../c-language/function-attributes.md), [třídu úložiště](../c-language/storage-class.md), [návratový typ](../c-language/return-type.md), [parametry](../c-language/parameters.md), a [tělo funkce](../c-language/function-body.md) součástí definice funkce podrobně popisují.

## <a name="see-also"></a>Viz také:

[Funkce](../c-language/functions-c.md)
