---
title: Upozornění (úroveň 3) C4635 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7651012d4c48d420734a9c6ec2ff051718f82007
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038110"
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