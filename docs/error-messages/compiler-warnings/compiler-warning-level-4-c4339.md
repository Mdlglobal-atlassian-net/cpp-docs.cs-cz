---
title: Upozornění (úroveň 4) C4339 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4339
dev_langs:
- C++
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab96374beffed9822b20f4f10db812f170ea6cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025227"
---
# <a name="compiler-warning-level-4-c4339"></a>Kompilátor upozornění (úroveň 4) C4339

'type': zjištěno použití nedefinovaného typu WinRT nebo CLR meta-data - použití tohoto typu může vést k výjimce modulu runtime

Typ není definovaný v kódu, který byl zkompilován pro prostředí Windows Runtime nebo modul common language runtime. Definice typu, aby se zabránilo možné běhovou výjimku.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4339 a ukazuje, jak ho opravit:

```
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```