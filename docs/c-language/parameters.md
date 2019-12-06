---
title: Parametry
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: f2fd4b49e08149f8ea5ce8fa6af46da39907dcf9
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857044"
---
# <a name="parameters"></a>Parametry

Argumenty jsou názvy hodnot předaných funkci voláním funkce. Parametry jsou hodnoty, které funkce očekává k přijetí. V prototypu funkce závorky následující po názvu funkce obsahují úplný seznam parametrů funkce a jejich typy. Deklarace parametrů určují typy, velikosti a identifikátory hodnot uložených v parametrech.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*– atribut<sub>opt</sub> *-SEQ* *deklarátor* *deklarace-list*<sub></sub> <sub>opt –</sub> *složený* příkaz

atribut /\* *– SEQ* je specifický pro Microsoft \*/

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatelem*<sub>opt</sub> *Direct-deklarátor*

*Direct-deklarátor*:/\* / funkce deklarátor \*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam parametrů typu* **)**  / \* deklarátor nový styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam identifikátorů*<sub>optimalizované</sub> **)**  / \* Obsolete – vizuální styl deklarátor \*/

*parametr-Type-list*:/\* \*seznamu parametrů /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* **,...**

*seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,** *deklarace parametru*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;*specifikátory deklarace* &nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *abstract-deklarátor*<sub>opt</sub>

*Parametr-Type-list* je posloupnost deklarací parametrů oddělených čárkami. Forma každého parametru v seznamu parametrů vypadá takto:

```C
[register]  type-specifier [declarator]
```

Parametry funkce deklarované s atributem **auto** generují chyby. Identifikátory parametrů se používají v těle funkce k odkazování na hodnoty předané do funkce. Parametry můžete pojmenovat v prototypu, ale názvy se na konci deklarace dostanou mimo rozsah. Proto lze názvy parametrů přiřadit stejným způsobem nebo jinak odlišně v definici funkce. Tyto identifikátory nelze předefinovat v vnějším bloku těla funkce, ale lze je předefinovat ve vnitřních vnořených blocích, jako by seznam parametrů byl nadřazeným blokem.

Každý identifikátor v *seznamu parametrů-typu* musí předcházet jeho vhodné specifikátoru typu, jak je znázorněno v následujícím příkladu:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Pokud je v seznamu parametrů k dispozici alespoň jeden parametr, může seznam končit čárkou následovanou třemi tečkami ( **,...** ). Tato konstrukce označovaná jako "Notation se třemi tečkami" označuje proměnný počet argumentů funkce. (Další informace naleznete v tématu [volání s proměnlivým počtem argumentů](../c-language/calls-with-a-variable-number-of-arguments.md) .) Nicméně volání funkce musí mít alespoň tolik argumentů, protože existují parametry před poslední čárkou.

Pokud do funkce nebudou předány žádné argumenty, je seznam parametrů nahrazen klíčovým slovem `void`. Toto použití `void` se liší od jeho použití jako specifikátoru typu.

Pořadí a typ parametrů, včetně jakéhokoliv použití notace tři tečky, musí být stejné ve všech deklaracích funkce (pokud existují) a v definici funkce. Typy argumentů po obvyklých aritmetických převodech musí být kompatibilní s typy odpovídajících parametrů. (Další informace o aritmetických převodech naleznete v tématu [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) .) Argumenty za třemi tečkami nejsou zaškrtnuté. Parametr může mít jakýkoli základní typ, strukturu, sjednocení, ukazatel nebo typ pole.

Kompilátor provádí běžné aritmetické převody nezávisle na každém parametru a v každém argumentu, pokud je to nutné. Po převodu není parametr kratší než `int`a žádný parametr nemá typ **float** , pokud není typ parametru explicitně zadán jako **float** v prototypu. To znamená, že například deklarace parametru jako `char` má stejný účinek jako `int`.

## <a name="see-also"></a>Viz také:

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
