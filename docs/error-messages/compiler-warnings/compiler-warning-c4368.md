---
title: Upozornění kompilátoru C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: b2af1166738d867c84ff4ebae832f831af7940ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485605"
---
# <a name="compiler-warning-c4368"></a>Upozornění kompilátoru C4368

nelze definovat 'člen' jako člen spravovaného 'typu': smíšené typy nejsou podporovány

Nativní datový člen nelze vložit do typu CLR.

Je však možné deklarovat ukazatel na nativní typ a řídit jeho dobu platnosti v konstruktoru, destruktoru a finalizační metodě spravované třídy. Další informace najdete v části [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Toto upozornění je vždy vyvoláno jako chyba. Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma k zakázání upozornění C4368.

## <a name="example"></a>Příklad

Následující ukázka generuje upozornění C4368.

```
// C4368.cpp
// compile with: /clr /c
struct N {};
ref struct O {};
ref struct R {
    R() : m_p( new N ) {}
    ~R() { delete m_p; }

   property N prop;   // C4368
   int i[10];   // C4368

   property O ^ prop2;   // OK
   N * m_p;   // OK
};
```