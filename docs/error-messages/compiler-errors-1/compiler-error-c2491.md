---
title: Chyba kompilátoru C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 3b48bebde6d7baedea73ed181cd4ea33adc44a69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361331"
---
# <a name="compiler-error-c2491"></a>Chyba kompilátoru C2491

'identifier': definice dllimport funkce není povolená

Data, statické datové členy a funkce mohou být deklarovány jako `dllimport`s, ale nebyl definován jako `dllimport`s.

Chcete-li tento problém vyřešit, odeberte `__declspec(dllimport)` specifikátor z definice funkce.

Následující ukázka generuje C2491:

```
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```