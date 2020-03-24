---
title: Upozornění kompilátoru C4368
ms.date: 11/04/2016
f1_keywords:
- C4368
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
ms.openlocfilehash: d96ae14bc427568dcf7ba7bc6e5d53f3d28883ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165299"
---
# <a name="compiler-warning-c4368"></a>Upozornění kompilátoru C4368

nelze definovat 'člen' jako člen spravovaného 'typu': smíšené typy nejsou podporovány

Nativní datový člen nelze vložit do typu CLR.

Je však možné deklarovat ukazatel na nativní typ a řídit jeho dobu platnosti v konstruktoru, destruktoru a finalizační metodě spravované třídy. Další informace naleznete v tématu [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Toto upozornění je vždy vyvoláno jako chyba. K zakázání C4368 Použijte direktivu pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4368.

```cpp
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
