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
ms.openlocfilehash: 0652fe6076899020050d94378649018721b4b188
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147227"
---
# <a name="parameters"></a>Parametry

Argumenty jsou názvy hodnotu předanou funkci volání funkce. Parametry jsou hodnoty, které funkce očekává. V prototypu funkce závorek za název funkce obsahuje úplný seznam parametrů funkce a jejich typy. Deklarace parametru určovat typy, velikostí a identifikátory hodnot uložených v parametrech.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*<sub>optimalizované</sub> *sekvence atributů*<sub>optimalizované</sub> *deklarátor* *seznam deklarací*  <sub>optimalizované</sub> *compound-statement*

/\* *sekvence atributů* je specifické pro Microsoft \*/

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*přímé declarator*: /\* deklarátorem funkce \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam parametrů typu* **)**  / \* deklarátor nový styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam identifikátorů*<sub>optimalizované</sub> **)**  / \* Obsolete – vizuální styl deklarátor \*/

*Seznam parametrů typu*: /\* seznam parametrů \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,...**

*Seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,** *deklarace parametru*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *deklarátorů*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *abstraktní deklarátor*<sub>optimalizované</sub>

*Seznam parametrů typu* je sekvence deklarací parametrů oddělených čárkami. Formulář každý parametr v seznamu parametrů vypadá takto:

```C
[register]  type-specifier [declarator]
```

Parametry funkce deklarované s **automaticky** atribut generují chyby. Identifikátory parametry se používají v těle funkce k odkazování na hodnoty předané funkci. Můžete pojmenovat parametrů v prototypu, ale názvy dostanou mimo rozsah na konci této deklarace. Proto názvy parametrů je možné přiřadit stejné způsobem nebo jinak než v definici funkce. Tyto identifikátory se nedá předefinovat v vnějšího bloku těla funkce, ale jejich lze redefinovat v vnitřní, vnořené bloky, jako by byl seznam parametrů z vnějšího bloku.

Každý identifikátor v *seznam parametrů typu* musí být uvozen specifikátorem jeho příslušného typu, jak je znázorněno v tomto příkladu:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

V případě alespoň jeden parametr v seznamu parametrů lze ukončit seznamu čárkou následovanou třemi tečkami (**;...** ). Tato konstrukce nazývá "zápis tří teček," Určuje proměnný počet argumentů funkce. (Viz [volání proměnlivým počtem argumentů](../c-language/calls-with-a-variable-number-of-arguments.md) Další informace.) Volání funkce však musí mít alespoň tolik argumentů jsou parametry před poslední čárkou.

Pokud mají být předány do funkce bez argumentů, seznam parametrů se nahrazuje klíčové slovo `void`. Toto použití `void` se liší od jeho použití jako specifikátoru typu.

Pořadí a typ parametrů, včetně veškeré jeho používání tento zápis tří teček musí být stejné ve všech deklarace funkcí (pokud existuje) a v definici funkce. Typy argumentů po obvyklé aritmetické převody musí být přiřazení kompatibilní s typy odpovídající parametry. (Viz [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) o aritmetické převody.) Argumenty za se třemi tečkami nekontrolují. Parametr může mít všechny základní struktury, sjednocení, ukazatele, nebo typ pole.

Kompilátor nezávisle na sobě provádí běžné aritmetické převody na každého parametru a na každý argument v případě potřeby. Po převodu je bez parametru kratší než `int`, a nemá žádný parametr **float** zadejte typ parametru není explicitně určena jako **float** v prototypu. To znamená, třeba deklarovat jako parametr `char` má stejný účinek jako ji jako deklarace `int`.

## <a name="see-also"></a>Viz také:

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
