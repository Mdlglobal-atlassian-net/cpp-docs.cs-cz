---
title: Chyba kompilátoru C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 4cb259ed0f43831226fb7e1a1ccf7b28bcef7819
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165200"
---
# <a name="compiler-error-c2868"></a>Chyba kompilátoru C2868

> "*identifikátor*': Neplatná syntaxe pro deklarace using; očekávaný název kvalifikovaný

A [using – deklarace](../../cpp/using-declaration.md) vyžaduje *kvalifikovaný název*, operátor rozsahu (`::`) oddělený sekvence názvů obor názvů, třídy nebo výčtu, která končí název identifikátoru. Operátor rozlišení oboru jednoho slouží k zavedení názvu v globálním oboru názvů.

## <a name="example"></a>Příklad

Následující ukázka generuje C2868 a také ukazuje správné použití:

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