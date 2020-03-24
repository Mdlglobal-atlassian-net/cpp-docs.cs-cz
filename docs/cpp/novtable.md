---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: d101e73f2f8d476c50b1b80b8daa7994151d43af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177830"
---
# <a name="novtable"></a>novtable

**Specifické pro společnost Microsoft**

Toto je **__declspec** rozšířený atribut.

Tato forma **__declspec** může být použita pro jakoukoliv deklaraci třídy, ale měla by být použita pouze na třídy čistě rozhraní, to znamená třídy, které nikdy nebudou vytvořeny sami. **__Declspec** zastaví kompilátor generování kódu pro inicializaci vfptr v konstruktorech a destruktoru třídy. V mnoha případech jsou tímto odebrány odkazy na tabulku vtable, které jsou přidruženy ke třídě a budou tedy odebrány linkerem. Použití této formy **__declspec** může vést k výraznému snížení velikosti kódu.

Pokud se pokusíte vytvořit instanci třídy **označené pomocí a** pak přistupovat ke členu třídy, obdržíte porušení přístupu (AV).

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
