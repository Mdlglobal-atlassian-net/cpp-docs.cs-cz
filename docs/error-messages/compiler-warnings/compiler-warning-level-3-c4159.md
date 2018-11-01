---
title: Kompilátor upozornění (úroveň 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: e898af8f109ed23bd1784df7b39c174bbed675f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552279"
---
# <a name="compiler-warning-level-3-c4159"></a>Kompilátor upozornění (úroveň 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>direktivy pragma pragma(pop,...): byl odebrán dřív nabízený identifikátor "*identifikátor*.

## <a name="remarks"></a>Poznámky

Obsahuje zdrojový kód **nabízených** instrukce s identifikátorem pro pragma, za nímž následuje **pop** bez identifikátoru. V důsledku toho *identifikátor* je odebrán a následné použití *identifikátor* může způsobit neočekávané chování.

## <a name="example"></a>Příklad

K tomuto upozornění předejít, poskytnout identifikátor **pop** instrukce. Příklad:

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```