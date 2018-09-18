---
title: Chyba kompilátoru C3510 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3510
dev_langs:
- C++
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5cc134823abf2657426b0c1be9cfbe6d92a74035
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111321"
---
# <a name="compiler-error-c3510"></a>Chyba kompilátoru C3510

Nelze najít závislý typ knihovny 'type_lib.

[no_registry s: %](../../preprocessor/no-registry.md) a [auto_search –](../../preprocessor/auto-search.md) bylo předáno `#import` , ale kompilátor nebyl schopen najít odkazovanou knihovnu typů.

Chcete-li vyřešit tuto chybu, ujistěte se, že všechny knihovny typů a odkazované knihovny typů jsou k dispozici pro kompilátor.

Následující ukázka generuje C3510:

Předpokládají, že byly vytvořeny následující knihovny dvou typů a že C3510a.tlb byl odstraněn nebo není v cestě.

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

A pak zdrojový kód pro druhý knihovny typů:

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

A pak kód klienta:

```
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```