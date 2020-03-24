---
title: Chyba kompilátoru C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 0cbcf7dc80aedc554594f88992059f98b7091c21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201630"
---
# <a name="compiler-error-c2868"></a>Chyba kompilátoru C2868

> '*Identifier*': Neplatná syntaxe pro using-Declaration; očekával se kvalifikovaný název.

[Deklarace using](../../cpp/using-declaration.md) vyžaduje *kvalifikovaný název*, operátor oboru (`::`) oddělenou sekvenci názvů oborů názvů, tříd nebo výčtů, které končí názvem identifikátoru. K zavedení názvu z globálního oboru názvů se dá použít operátor rozlišení s jedním oborem.

## <a name="example"></a>Příklad

Následující ukázka vygeneruje C2868 a také zobrazí správné použití:

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```
