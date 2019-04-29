---
title: Kompilátor upozornění (úroveň 1) C4160
ms.date: 08/27/2018
f1_keywords:
- C4160
helpviewer_keywords:
- C4160
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
ms.openlocfilehash: 988c1fcbe0826582dceaa527811c688711fd8906
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391839"
---
# <a name="compiler-warning-level-1-c4160"></a>Kompilátor upozornění (úroveň 1) C4160

> #<a name="pragma-pop--did-not-find-previously-pushed-identifier-identifier"></a>direktivy pragma (pop,...): nebyl nalezen dřív nabízený identifikátor "*identifikátor*.

## <a name="remarks"></a>Poznámky

Příkaz – Direktiva pragma ve zdrojovém kódu se pokusí vyvolat přes pop identifikátor, který nebylo vloženo. K tomuto upozornění předejít, ujistěte se, že je odebrán identifikátor má správně vložena.

## <a name="example"></a>Příklad

Následující příklad generuje C4160 a ukazuje, jak ho opravit:

```cpp
// C4160.cpp
// compile with: /W1
#pragma pack(push)

#pragma pack(pop, id)   // C4160
// use identifier when pushing to resolve the warning
// #pragma pack(push, id)

int main() {
}
```