---
title: Chyba kompilátoru C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: 3f9dea77b739aa59474e60cf852fff2577ab6ba9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753624"
---
# <a name="compiler-error-c3510"></a>Chyba kompilátoru C3510

Nejde najít závislou knihovnu typů type_lib.

[no_registry](../../preprocessor/no-registry.md) a [auto_search](../../preprocessor/auto-search.md) byly předány do `#import` ale kompilátor nedokázal najít odkazovanou knihovnu typů.

Chcete-li tuto chybu vyřešit, zajistěte, aby byl pro kompilátor k dispozici všechny knihovny typů a odkazované knihovny typů.

Následující ukázka generuje C3510:

Předpokládejme, že byly sestaveny následující dvě knihovny typů a zda se C3510a. tlb odstranila nebo ne na cestě.

```
// C3510a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C3510aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C3510
   {
      one, two, three
   };
};
```

A pak zdrojový kód druhé knihovny typů:

```
// C3510b.idl
// post-build command: del /f C3510a.tlb
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
library C3510bLib
{
   importlib ("C3510a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
   struct S_C3510 {
      enum E_C3510 e;
   };
};
```

A pak klientský kód:

```cpp
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```
