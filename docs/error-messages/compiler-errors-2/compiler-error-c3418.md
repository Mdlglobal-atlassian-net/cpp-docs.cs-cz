---
title: Chyba kompilátoru C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 8456e9b17b72cd4ac98349d2f2871a1c59f56911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311487"
---
# <a name="compiler-error-c3418"></a>Chyba kompilátoru C3418

specifikátor přístupu "specifikátor" není podporován.

Specifikátor přístupu CLR byl nesprávně zadán.  Další informace najdete v tématu viditelnost typů a členů viditelnost v [jak: Definice a používání tříd a struktur (C++vyhodnocovací)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3418.

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```