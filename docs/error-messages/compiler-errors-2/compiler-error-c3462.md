---
title: Chyba kompilátoru C3462
ms.date: 11/04/2016
f1_keywords:
- C3462
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
ms.openlocfilehash: 56227f124d49630d8776f291ada302bd6cd6e983
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756601"
---
# <a name="compiler-error-c3462"></a>Chyba kompilátoru C3462

' type ': je možné přeslat pouze importovaný typ.

Atribut TypeForwardedTo musí být použit pro typ v odkazovaných metadatech.

Další informace naleznete v tématu [předávání typů (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu.

```cpp
// C3462.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3462.

```cpp
// C3462b.cpp
// compile with: /clr /c
#using "C3462.dll"
ref class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3462
[assembly:TypeForwardedTo(R::typeid)];
```
