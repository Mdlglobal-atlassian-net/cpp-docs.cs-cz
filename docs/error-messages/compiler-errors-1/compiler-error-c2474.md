---
title: Chyba kompilátoru C2474
ms.date: 11/04/2016
f1_keywords:
- C2474
helpviewer_keywords:
- C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
ms.openlocfilehash: c49f38b828a41c72135ba9182d4d0f5eee4df1de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350881"
---
# <a name="compiler-error-c2474"></a>Chyba kompilátoru C2474

! – klíčové slovo': chybí sousední středník, může být buď klíčové slovo nebo identifikátor.

Kompilátor Očekávalo se nalezení středník a nebyl schopen určit vašich představ. Přidáte středník pro vyřešení této chyby.

## <a name="example"></a>Příklad

Následující ukázka generuje C2474.

```
// C2474.cpp
// compile with: /clr /c

ref class A {
   ref class B {}
   property int i;   // C2474 error
};

// OK
ref class B {
   ref class D {};
   property int i;
};

ref class E {
   ref class F {} property;
   int i;
};
```