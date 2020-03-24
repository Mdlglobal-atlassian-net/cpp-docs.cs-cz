---
title: Upozornění kompilátoru (úroveň 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 859ff75bbd4b3fe248d9658495e64c0c039fbb40
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186410"
---
# <a name="compiler-warning-level-1-c4540"></a>Upozornění kompilátoru (úroveň 1) C4540

dynamic_cast slouží k převodu na nedostupný nebo nejednoznačný základ; test za běhu se nezdařil ("typ1" na "typ2")

Použili jste `dynamic_cast` k převodu z jednoho typu na jiný. Kompilátor zjistil, že přetypování by vždy selže (vrátí **hodnotu null**), protože základní třída je nepřístupná (`private`, například) nebo dvojznačná (v hierarchii tříd se objevuje více než jednou).

V následujícím příkladu vidíte příklad tohoto upozornění. Třída **B** je odvozena od třídy **A**. Program používá `dynamic_cast` k přetypování z třídy **B** (odvozené třídy) na třídu **A**, což bude vždy neúspěšné, protože třída **B** je `private` a tudíž nepřístupná. Změna přístupu **typu** na **veřejnou** vyřeší upozornění.

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```
