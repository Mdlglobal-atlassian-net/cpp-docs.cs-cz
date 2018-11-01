---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: 9dcca6ec07a19d53da238020805299b652cbf919
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630240"
---
# <a name="novtable"></a>novtable

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Jedná se **__declspec** rozšířeného atributu.

Tato forma **__declspec** lze použít pro všechny deklarace tříd, ale bude použito pouze na rozhraní třídy, tedy třídy, které se nikde nebude vytvořena instance samostatně. **__Declspec** zastaví kompilátoru generování kódu inicializace konstruktoru vfptr a destruktoru třídy. V mnoha případech jsou tímto odebrány odkazy na tabulku vtable, které jsou přidruženy ke třídě a budou tedy odebrány linkerem. Použití této formy atributu **__declspec** může vést k významnému snížení velikosti kódu.

Při pokusu o vytvoření instance třídy označené **novtable** a poté přístup člena třídy, zobrazí se narušení přístupu (AV).

## <a name="example"></a>Příklad

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)