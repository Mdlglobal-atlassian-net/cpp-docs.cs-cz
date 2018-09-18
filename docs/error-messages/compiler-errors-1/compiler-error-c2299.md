---
title: Chyba kompilátoru C2299 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4977f4a5ac81cf4c04d3b143f6f7e670a9d9279
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049615"
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