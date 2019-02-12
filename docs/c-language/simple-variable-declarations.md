---
title: Deklarace jednoduchých proměnných
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 27710dabe512332564ee557a9d022457d9fddc5c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149983"
---
# <a name="simple-variable-declarations"></a>Deklarace jednoduchých proměnných

Deklarace jednoduchých proměnné, nejjednodušší forma deklarátoru s přímým přístupem, určuje typ a název proměnné. Také určuje třídu úložiště proměnné a datové typy.

Třídy úložiště nebo typy (nebo obojí) se vyžadují v deklaracích proměnných. Netypová proměnné (jako například `var;`) generovat upozornění.

## <a name="syntax"></a>Syntaxe

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*

*identifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* *nenumerickému*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* *číslice*

Aritmetický, struktura, sjednocení, výčty a void typy a typy reprezentována `typedef` názvy, jednoduché deklarátory můžete použít v deklaraci, protože specifikátor typu poskytuje psaní informace. Ukazatel, pole a typy funkce vyžadují složitějších deklarátorů.

Můžete použít seznam identifikátorů oddělených čárkami (**,**) k určení několika proměnných ve stejné deklaraci. Všechny proměnné definované v deklaraci mají stejné základního typu. Příklad:

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

Proměnné `x` a `y` můžou obsahovat libovolnou hodnotu do množiny definované `int` typ pro danou implementaci. Jednoduchý objekt `z` je inicializován na hodnotu 1 a není možné upravit.

Pokud deklarace `z` byla pro neinicializovaného statická proměnná nebo byla v rozsahu souboru, získá počáteční hodnotu 0 a tato hodnota by neupravitelných.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

V tomto příkladu, proměnných, `reply` a `flag`, mají `unsigned long` zadejte a podržte nepodepsaných integrálních hodnot.

## <a name="see-also"></a>Viz také:

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
