---
title: Upozornění kompilátoru (úroveň 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: be79c664f09f80d8f0c8779babf236dccac90ea8
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626233"
---
# <a name="compiler-warning-level-1-c4183"></a>Upozornění kompilátoru (úroveň 1) C4183

' identifier ': chybějící návratový typ; Předpokládá se, že se jedná o členskou funkci, která vrací int.

Vložená definice členské funkce ve třídě nebo struktuře nemá návratový typ. Tato členská funkce předpokládá, že má výchozí návratový typ `int`.

Následující ukázka generuje C4183:

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```