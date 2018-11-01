---
title: Chyba kompilátoru C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 4776ddede31dbcebe56a5919fd111f4df7248215
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590005"
---
# <a name="compiler-error-c2299"></a>Chyba kompilátoru C2299

'function': Změna chování: explicitní specializace nemůže být kopírovací konstuktor ani operátor copy assignment

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: předchozí verze aplikace Visual C++ explicitní specializace povolená pro kopírovací konstuktor ani operátor přiřazení kopie.

Chcete-li vyřešit C2299, Nedovolte, aby byly kopírovací konstruktor nebo operátor přiřazení šablony funkce, ale spíše nešablonové funkce, která přebírá typ třídy. Veškerý kód, který volá kopírovací konstuktor ani operátor přiřazení explicitním zadáním argumentů šablony musí odebrat argumenty šablony.

Následující ukázka generuje C2299:

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```