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

Argumenty jsou názvy hodnot předaných funkci voláním funkce. Parametry jsou hodnoty, které funkce očekává. V prototypu funkce obsahují závorky za názvem funkce úplný seznam parametrů funkce a jejich typů. Deklarace parametrů určují typy, velikosti a identifikátory hodnot uložených v parametrech.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace specifikátory*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**atribut-seq* je specifický pro společnost Microsoft\*/

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel*<sub>opt</sub> *direct-declarator*

*přímý deklarátor*\* : / Deklarátor funkce\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator***(***parametr-type-list***)**  / \* Deklarátor nového stylu      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator***(***identifier-list*<sub>opt</sub> **)**  / \* Deklarátor zastaralého stylu    \*/

*seznam parametrů*typu :\* / Seznam parametrů\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* **, ...**

*seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* **,**  *deklarace parametrů*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor* *specifikátorů deklarací*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*volba* *abstraktně specifikátorů*<sub>deklarací deklarací deklarací deklarací deklarací</sub>

*Seznam typu parametru* je posloupnost deklarací parametrů oddělených čárkami. Forma každého parametru v seznamu parametrů vypadá takto:

```C
[register]  type-specifier [declarator]
```

Parametry funkce deklarované s **automatickým** atributem generují chyby. Identifikátory parametrů se používají v těle funkce odkazovat na hodnoty předané funkci. Parametry v prototypu můžete pojmenovat, ale názvy jsou mimo rozsah na konci deklarace. Proto mohou být názvy parametrů přiřazeny stejným způsobem nebo odlišně v definici funkce. Tyto identifikátory nelze předefinovat v nejvzdálenějším bloku těla funkce, ale mohou být předefinovány ve vnitřních vnořených blocích, jako by seznam parametrů byl ohraničujícíblok.

Každému identifikátoru v *seznamu typů parametrů* musí předcházet jeho příslušný specifikátor typu, jak je znázorněno v tomto příkladu:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Pokud v seznamu parametrů dojde alespoň k jednomu parametru, může seznam končit čárkou následovanou třemi tečkami (**, ...**). Tato konstrukce, nazývaná "zápis se třemi tečkami", označuje proměnný počet argumentů funkce. (Další informace naleznete [v tématu Volání s proměnným počtem argumentů.)](../c-language/calls-with-a-variable-number-of-arguments.md) Volání funkce však musí mít alespoň tolik argumentů, kolik je parametrů před poslední čárkou.

Pokud nemají být funkci předány žádné argumenty, bude seznam parametrů `void`nahrazen klíčovým slovem . Toto `void` použití je odlišné od jeho použití jako specifikátor typu.

Pořadí a typ parametrů, včetně použití zápisu se třemi tečkami, musí být stejné ve všech deklaracích funkcí (pokud existuje) a v definici funkce. Typy argumentů po obvyklých aritmetických převodech musí být kompatibilní s typy odpovídajících parametrů. (Informace o aritmetických konverzích naleznete v tématu [Obvyklé aritmetické převody.)](../c-language/usual-arithmetic-conversions.md) Argumenty následující tři tečky nejsou kontrolovány. Parametr může mít libovolný základní, struktura, sjednocení, ukazatel nebo typ pole.

Kompilátor provádí obvyklé aritmetické převody nezávisle na každém parametru a na každém argumentu, v případě potřeby. Po převodu žádný parametr `int`je kratší než , a žádný parametr má **plovoucí** typ, pokud typ parametru je explicitně zadán jako **float** v prototypu. To například znamená, že deklarování parametru jako parametru `char` `int`má stejný účinek jako deklarování jako .

## <a name="see-also"></a>Viz také

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
