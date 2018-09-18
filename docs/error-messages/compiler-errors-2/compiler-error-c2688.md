---
title: Chyba kompilátoru C2688 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2688
dev_langs:
- C++
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 729cedf532621bf9c65014cb8d92f3a262f399fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033093"
---
# <a name="compiler-error-c2688"></a>Chyba kompilátoru C2688

'C2::fgrv': kovariant se vrací s několika nebo virtual, což není podporované funkcemi varargs

Kovariantní návratové typy nejsou podporovány v aplikaci Visual C++, když funkce obsahuje argumenty proměnných.

Chcete-li vyřešit tuto chybu, definujte vaší funkce tak, aby používat proměnné argumenty nebo zkontrolujte vrácené hodnoty stejný pro všechny virtuální funkce.

Následující ukázka generuje C2688:

```
// C2688.cpp
struct G1 {};
struct G2 {};
struct G3 : G1, G2 {};
struct G4 {};
struct G5 {};
struct G6 : G4, G5 {};
struct G7 : G3, G6 {};

struct C1 {
   virtual G4& fgrv(int,...);
};

struct C2 : C1 {
   virtual G7& fgrv(int,...);   // C2688, does not return G4&
};
```