---
title: Upozornění kompilátoru C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: ddc0d1968ae373ff1e81c98a513e6f84fdb885e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165324"
---
# <a name="compiler-warning-c4355"></a>Upozornění kompilátoru C4355

'this' : použito v inicializačním seznamu základních členů

**Tento** ukazatel je platný pouze v rámci nestatických členských funkcí. Nedá se použít v seznamu inicializátorů pro základní třídu.

Konstruktory základní třídy a konstruktory členů třídy jsou volány před **tímto** konstruktorem. V důsledku toho jste předali ukazatel na nesestavený objekt na jiný konstruktor. Pokud tyto další konstruktory přistupují ke všem členům nebo je členské funkce volat, výsledek nebude definován. **Tento** ukazatel byste neměli používat, dokud se nedokončí všechny konstrukce.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4355:

```cpp
// C4355.cpp
// compile with: /w14355 /c
#include <tchar.h>

class CDerived;
class CBase {
public:
   CBase(CDerived *derived): m_pDerived(derived) {};
   ~CBase();
   virtual void function() = 0;

   CDerived * m_pDerived;
};

class CDerived : public CBase {
public:
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor
   virtual void function() {};
};

CBase::~CBase() {
   m_pDerived -> function();
}

int main() {
   CDerived myDerived;
}
```
