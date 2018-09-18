---
title: Upozornění (úroveň 1) C4540 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e3f553bd1f910c7b17e079dc1f03664c78383e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042764"
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