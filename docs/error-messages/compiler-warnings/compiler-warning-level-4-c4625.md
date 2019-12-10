---
title: Upozornění kompilátoru (úroveň 4) C4625
ms.date: 11/04/2016
f1_keywords:
- C4625
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
ms.openlocfilehash: d98e295a9a48da16b58202bc172e112b5c0287d9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990707"
---
# <a name="compiler-warning-level-4-c4625"></a>Upozornění kompilátoru (úroveň 4) C4625

odvozená třída: konstruktor Copy byl implicitně definovaný jako odstraněný, protože konstruktor kopie základní třídy je nedostupný nebo odstraněný.

Kopírovací konstruktor byl odstraněn nebo není přístupný v základní třídě, a proto nebyl vygenerován pro odvozenou třídu. Jakýkoli pokus o zkopírování objektu tohoto typu způsobí chybu kompilátoru.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4625 a ukazuje, jak ji opravit.

```cpp
// C4625.cpp
// compile with: /W4 /c
#pragma warning(default : 4625)

struct A {
   A() {}

private:
   A(const A&) {}
};

struct C : private virtual A {};
struct B :  C {};   // C4625 no copy constructor

struct D : A {};
struct E :  D {};   // OK
```
