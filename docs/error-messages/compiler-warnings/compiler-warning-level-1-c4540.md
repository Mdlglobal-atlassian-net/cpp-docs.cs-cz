---
title: Kompilátor upozornění (úroveň 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 86f6cd866f7708277ebba436ba7c076086dc9c8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473668"
---
# <a name="compiler-warning-level-1-c4540"></a>Kompilátor upozornění (úroveň 1) C4540

dynamic_cast slouží k převodu do nedostupný nebo nejednoznačný základní; test za běhu selže ('type1' na 'type2')

Použili jste `dynamic_cast` pro převod z jednoho typu na jiný. Kompilátor Určuje, že přetypování vždy selže (vrátit **NULL**) protože základní třída je nedostupná (`private`, například) nebo nejednoznačný (zobrazí se více než jednou v hierarchii tříd pro instanci).

Následuje příklad toto upozornění. Třída **B** je odvozena z třídy **A**. Program používá `dynamic_cast` přetypovat z třídy **B** (odvozená třída) do třídy **A**, která vždy selže, protože třída **B** je `private` . proto nedostupné. Mění se přístup z **A** k **veřejné** vyřeší upozornění.

```
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