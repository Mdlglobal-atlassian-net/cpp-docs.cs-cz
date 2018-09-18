---
title: Chyba kompilátoru C2868 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2de22b34f9dc564ef89d7776af86718af70d51eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037863"
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