---
title: Chyba kompilátoru C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 117c9b9918950fd2e95e206c5aea457dee183b0a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781572"
---
# <a name="compiler-error-c3465"></a>Chyba kompilátoru C3465

určený typ 'type' musí odkazovat na sestavení 'assembly'

Předávání typů bude fungovat pro klientskou aplikaci, dokud je provedena rekompilace klienta. Při opětovné kompilaci, budete potřebovat odkaz pro všechna sestavení, který obsahuje definici typu, který se používá v klientské aplikaci.

Další informace najdete v tématu [předávání typů (C + +/ CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří sestavení, která obsahuje nové umístění typu.

```
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Příklad

Následující příklad vytvoří sestavení, který se používá pro jiné definice typu, ale nyní obsahuje syntaxi předávání typu.

```
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3465.

```
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```