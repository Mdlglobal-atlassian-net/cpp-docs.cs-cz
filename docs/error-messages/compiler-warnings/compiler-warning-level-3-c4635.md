---
title: Kompilátor upozornění (úroveň 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: 21873a883b19924ce3ef41511d65f8ae640875f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479232"
---
# <a name="compiler-warning-level-3-c4635"></a>Kompilátor upozornění (úroveň 3) C4635

Cíl komentáře dokumentu XML: chybně vytvořený kód XML: důvod

Kompilátor nalezen problém s značky XML.  Opravte problém a překompilujte

Následující ukázka generuje C4635:

```
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

Všimněte si, že výstup pro tuto ukázku: **koncová značka 'member' neodpovídá počáteční značce "Přehled".**

Problém s této ukázce se koncová značka pro \<summary > je nesprávně, a kompilátor nedokáže rozpoznat jako \<summary > koncová značka.  \<Člena > značky vložené do souboru .xdc kompilátorem v každé/doc kompilaci.  Ano, problémem je, že koncovou značku \</member >, se neshoduje s předchozí počáteční značku, kompilátor zpracovává (\<summary >.