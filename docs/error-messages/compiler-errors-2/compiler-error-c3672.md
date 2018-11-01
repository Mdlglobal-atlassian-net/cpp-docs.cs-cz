---
title: Chyba kompilátoru C3672
ms.date: 11/04/2016
f1_keywords:
- C3672
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
ms.openlocfilehash: 36048f3e4b8cc1be3e766f11b5c131513a3365da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436774"
---
# <a name="compiler-error-c3672"></a>Chyba kompilátoru C3672

výraz pseudo-destructor jde použít jenom jako součást volání funkce

Destruktor se volá se nesprávně.  Další informace najdete v tématu [destruktory](../../cpp/destructors-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3672.

```
// C3672.cpp
template<typename T>
void f(T* pT) {
   &pT->T::~T;   // C3672
   pT->T::~T();   // OK
};

int main() {
   int i;
   f(&i);
}
```