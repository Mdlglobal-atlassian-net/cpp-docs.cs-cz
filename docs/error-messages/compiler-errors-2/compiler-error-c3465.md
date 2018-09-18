---
title: Chyba kompilátoru C3465 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3465
dev_langs:
- C++
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6aa388d95904aecc8e1ba558b374249bb280e02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048978"
---
# <a name="compiler-error-c3465"></a>Chyba kompilátoru C3465

určený typ 'type' musí odkazovat na sestavení 'assembly'

Předávání typů bude fungovat pro klientskou aplikaci, dokud je provedena rekompilace klienta. Při opětovné kompilaci, budete potřebovat odkaz pro všechna sestavení, který obsahuje definici typu, který se používá v klientské aplikaci.

Další informace najdete v tématu [předávání typů (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).

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