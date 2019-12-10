---
title: Upozornění kompilátoru (úroveň 4) C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: 4d0dd9aec19fb21870a1233cd3b713337fa15aaa
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990641"
---
# <a name="compiler-warning-level-4-c4623"></a>Upozornění kompilátoru (úroveň 4) C4623

`derived class`: výchozí konstruktor byl implicitně definovaný jako odstraněný, protože výchozí konstruktor základní třídy je nedostupný nebo odstraněný.

Konstruktor nebyl přístupný v základní třídě a nebyl vygenerován pro odvozenou třídu. Jakékoli pokus o vytvoření objektu tohoto typu v zásobníku způsobí chybu kompilátoru.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4623.

```cpp
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```
