---
title: Chyba kompilátoru C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 009a441ec610053176e79126d9f2663f29b26bc6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759045"
---
# <a name="compiler-error-c2299"></a>Chyba kompilátoru C2299

' function ': Změna chování: explicitní specializace nemůže být kopírovacím konstruktorem nebo operátorem přiřazení kopírování

Tato chyba se může vygenerovat taky v důsledku práce s vyhovujícími kompilátory, která se dokončila pro Visual Studio 2005: předchozí verze C++ vizuálu povolila explicitní specializace kopírovacího konstruktoru nebo operátoru přiřazení pro kopírování.

Chcete-li vyřešit C2299, nevytvářejte konstruktor kopírování ani operátor přiřazení funkce šablony, ale spíše nešablonou funkce, která přebírá typ třídy. Jakýkoli kód, který volá kopírovací konstruktor nebo operátor přiřazení explicitním zadáním argumentů šablony, je nutné odebrat argumenty šablony.

Následující ukázka generuje C2299:

```cpp
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```
