---
title: Upozornění (úroveň 4) C4625 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4625
dev_langs:
- C++
helpviewer_keywords:
- C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 970321370aeeea0ca4324f9a25d3ee1d8e54e15e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069102"
---
# <a name="compiler-warning-level-4-c4625"></a>Kompilátor upozornění (úroveň 4) C4625

'derived class': kopírovací konstuktor byl implicitně definovaný jako odstranit, protože kopírovací konstruktor základní třídy je nedostupné nebo odstraněné

Kopírovací konstruktor se odstranil nebo není k dispozici v základní třídě a proto se nevygeneroval pro odvozenou třídu. Jakýkoliv pokus o kopírování objektu tohoto typu způsobí chybu kompilátoru.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C4625 a ukazuje, jak ho opravit.

```
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