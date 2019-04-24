---
title: Upozornění kompilátoru C4355
ms.date: 11/04/2016
f1_keywords:
- C4355
helpviewer_keywords:
- C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
ms.openlocfilehash: 6b74c8dd5ce9860cb218d21790f12ba05e9be22f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151822"
---
# <a name="compiler-warning-c4355"></a>Upozornění kompilátoru C4355

'this' : použito v inicializačním seznamu základních členů

**To** ukazatel je platný pouze v rámci nestatické členské funkce. Nelze použít v seznamu inicializátorů pro základní třídu.

Konstruktory základní třídy a konstruktory členů třídy se nazývají před **to** konstruktoru. V důsledku toho jsme předán ukazatel unconstructed objektu do jiného konstruktoru. Pokud tyto konstruktory přístup k žádné členy nebo volat členské funkce na to, bude výsledek nedefinovaný. Neměli byste používat **to** ukazatele, dokud se nedokončí všechny konstrukce.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4355:

```
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