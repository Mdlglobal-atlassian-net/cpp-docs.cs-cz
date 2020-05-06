---
title: Deklarace jednoduchých proměnných
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 27710dabe512332564ee557a9d022457d9fddc5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158233"
---
# <a name="simple-variable-declarations"></a>Deklarace jednoduchých proměnných

Deklarace jednoduché proměnné, nejjednodušší forma přímé deklarátor, určuje název a typ proměnné. Určuje také třídu úložiště proměnné a datový typ.

Pro deklarace proměnných jsou požadovány třídy úložiště nebo typy (nebo obojí). Netypové proměnné (například `var;`) generují upozornění.

## <a name="syntax"></a>Syntaxe

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*přímý – deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*

*identifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nenumerickému*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nečíselný* identifikátor<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*číslice* *identifikátoru*

Pro aritmetické, struktury, sjednocení, výčty a typy void a pro typy reprezentované `typedef` jednoduchým deklarátory lze použít v deklaraci, protože specifikátor typu poskytuje všechny informace o zápisu. Typy ukazatelů, polí a funkcí vyžadují složitější deklarátory.

Seznam identifikátorů oddělených čárkami (**,**) můžete použít k určení několika proměnných ve stejné deklaraci. Všechny proměnné definované v deklaraci mají stejný základní typ. Příklad:

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

Proměnné `x` a `y` mohou obsahovat libovolnou hodnotu v sadě definované `int` typem pro konkrétní implementaci. Jednoduchý objekt `z` je inicializován na hodnotu 1 a nelze jej upravovat.

Pokud `z` byla deklarace pro neinicializovaná statickou proměnnou nebo byla v rozsahu souboru, obdrží počáteční hodnotu 0 a tato hodnota by nebyla upravitelná.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

V tomto příkladu jsou proměnné `reply` a `flag`, mají `unsigned long` typ a uchovávají celočíselné hodnoty bez znaménka.

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
