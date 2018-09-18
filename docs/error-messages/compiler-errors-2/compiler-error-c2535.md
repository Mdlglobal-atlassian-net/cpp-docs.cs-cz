---
title: Chyba kompilátoru C2535 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98e1920b2163a318fbdba3b64d56bf74a8cd809f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085896"
---
# <a name="compiler-error-c2535"></a>Chyba kompilátoru C2535

'identifikátor': členská funkce je již definována nebo deklarována

Tato chyba může být způsobena použitím stejného seznamu formálních parametrů ve více než jedné definici nebo deklaraci přetížené funkce.

Pokud jste c2535 zobrazí z důvodu funkce Dispose, přečtěte si téma [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Další informace.

Pokud kompilujete projekt knihovny ATL, další informace naleznete v článku Q241852 znalostní báze.

Následující ukázka generuje C2535:

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```