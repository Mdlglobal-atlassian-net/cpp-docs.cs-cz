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
- ellipsis (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 78ad91ea86d81a3b6d888335ba7b78399a1d2aea
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032067"
---
# <a name="parameters"></a>Parametry

Argumenty jsou názvy hodnot předaných funkci voláním funkce. Parametry jsou hodnoty, které funkce očekává k přijetí. V prototypu funkce závorky následující po názvu funkce obsahují úplný seznam parametrů funkce a jejich typy. Deklarace parametrů určují typy, velikosti a identifikátory hodnot uložených v parametrech.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory*<sub>opt</sub> *atribut – seq*<sub>opt</sub> *deklarátor* *deklarace-list*<sub>opt</sub> – *složený* příkaz

/\**atribut – seq* je specifický pro společnost Microsoft\*/

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*Direct-deklarátor*:/\* A – funkce deklarátor\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***(***parametr-Type-list***)**  / \* – nový styl deklarátor      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***(opt***-list*<sub>opt</sub> **)**  / \* zastaralý styl deklarátor    \*/

*seznam parametrů-typu*:/\* seznam parametrů\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* **,...**

*seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* **,**  *parametr-Declaration*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory* *deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace-specifikátory* *abstract-deklarátor*<sub>opt</sub>

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

Pokud je v seznamu parametrů k dispozici alespoň jeden parametr, může seznam končit čárkou následovanou třemi tečkami (**,...**). Tato konstrukce označovaná jako "Notation se třemi tečkami" označuje proměnný počet argumentů funkce. (Další informace naleznete v tématu [volání s proměnlivým počtem argumentů](../c-language/calls-with-a-variable-number-of-arguments.md) .) Nicméně volání funkce musí mít alespoň tolik argumentů, protože existují parametry před poslední čárkou.

Pokud do funkce nebudou předány žádné argumenty, je seznam parametrů nahrazen klíčovým slovem `void`. Toto použití `void` je odlišné od svého použití jako specifikátor typu.

Pořadí a typ parametrů, včetně jakéhokoliv použití notace tři tečky, musí být stejné ve všech deklaracích funkce (pokud existují) a v definici funkce. Typy argumentů po obvyklých aritmetických převodech musí být kompatibilní s typy odpovídajících parametrů. (Další informace o aritmetických převodech naleznete v tématu [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) .) Argumenty za třemi tečkami nejsou zaškrtnuté. Parametr může mít jakýkoli základní typ, strukturu, sjednocení, ukazatel nebo typ pole.

Kompilátor provádí běžné aritmetické převody nezávisle na každém parametru a v každém argumentu, pokud je to nutné. Po převodu žádný parametr není kratší než a žádný `int`parametr nemá typ **float** , pokud není typ parametru explicitně zadaný jako **float** v prototypu. To znamená, že například, který deklaruje parametr jako `char` má stejný účinek jako deklarace jako. `int`

## <a name="see-also"></a>Viz také

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
