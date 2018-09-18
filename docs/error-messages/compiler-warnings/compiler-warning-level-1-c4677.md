---
title: Upozornění (úroveň 1) C4677 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4677
dev_langs:
- C++
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6a3f57ba0e3d4c15c83711a86bb8482fa8b0596
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049382"
---
# <a name="compiler-warning-level-1-c4677"></a>Kompilátor upozornění (úroveň 1) C4677

'function': podpis nesoukromého členu obsahuje typ sestavení private 'private_type.

Typ, který nemá přístupnost public mimo sestavení používá typ, který má privátní přístup mimo sestavení. Komponenta, která odkazuje na typ veřejné sestavení nebude možné používat typ člena nebo členy, které odkazují na typ sestavení private.

## <a name="example"></a>Příklad

Následující ukázka generuje C4677.

```
// C4677.cpp
// compile with: /clr /c /W1
delegate void TestDel();
public delegate void TestDel2();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;   // C4677
   static event TestDel2^ MyClass_Event2;   // OK
};
```