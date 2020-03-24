---
title: Upozornění kompilátoru (úroveň 1) C4364
ms.date: 11/04/2016
f1_keywords:
- C4364
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
ms.openlocfilehash: 79c8809b4de9d6853aaacec4283bf01d0e89305e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187099"
---
# <a name="compiler-warning-level-1-c4364"></a>Upozornění kompilátoru (úroveň 1) C4364

\#použití pro sestavení ' file ' dříve zobrazené v umístění (line_number) bez atributu as_friend; as_friend se nepoužívá.

Pro daný soubor metadat byla opakována `#using` direktiva, ale kvalifikátor `as_friend` nebyl použit v prvním výskytu; Kompilátor bude ignorovat druhý `as_friend`.

Další informace naleznete v tématu [Friend Assemblies (C++)](../../dotnet/friend-assemblies-cpp.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu.

```cpp
// C4364.cpp
// compile with: /clr /LD
ref class A {};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4364.

```cpp
// C4364_b.cpp
// compile with: /clr /W1 /c
#using " C4364.dll"
#using " C4364.dll" as_friend   // C4364
```
