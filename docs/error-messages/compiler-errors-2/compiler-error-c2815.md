---
title: Chyba kompilátoru C2815
ms.date: 11/04/2016
f1_keywords:
- C2815
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
ms.openlocfilehash: ab6708e7ae0a56bd71adebad4fb42d6ea9abe116
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175404"
---
# <a name="compiler-error-c2815"></a>Chyba kompilátoru C2815

operátor delete: první formální parametr musí být "void *', 'param' byl však použit

Všechny uživatelem definované [operátor delete](../../standard-library/new-operators.md#op_delete) funkce musí přebírat první formální parametr typu `void *`.

Následující ukázka generuje C2815:

```
// C2815.cpp
// compile with: /c
class CMyClass {
public:
   void mf1(int *a);
   void operator delete(CMyClass *);   // C2815
   void operator delete(void *);
};
```