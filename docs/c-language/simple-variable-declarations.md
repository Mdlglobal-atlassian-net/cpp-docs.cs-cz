---
title: Deklarace jednoduchých proměnných | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7216a4a470b6293a31d6f364626188e41351b5cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763136"
---
# <a name="simple-variable-declarations"></a>Deklarace jednoduchých proměnných

Deklarace jednoduchých proměnné, nejjednodušší forma deklarátoru s přímým přístupem, určuje typ a název proměnné. Také určuje třídu úložiště proměnné a datové typy.

Třídy úložiště nebo typy (nebo obojí) se vyžadují v deklaracích proměnných. Netypová proměnné (jako například `var;`) generovat upozornění.

## <a name="syntax"></a>Syntaxe

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel*<sub>optimalizované</sub> *direct-declarator*

*přímé declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*

*identifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nenumerickému*<br/>
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

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)