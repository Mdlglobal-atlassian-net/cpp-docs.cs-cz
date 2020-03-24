---
title: Upozornění kompilátoru (úroveň 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: c7a2d72b429f762e476286093c7f273a9a546cb6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174671"
---
# <a name="compiler-warning-level-1-c4917"></a>Upozornění kompilátoru (úroveň 1) C4917

' deklarátor ': identifikátor GUID lze přidružit pouze k třídě, rozhraní nebo oboru názvů.

Uživatelsky definovaná struktura jiná než [Třída](../../cpp/class-cpp.md), [rozhraní](../../cpp/interface.md)nebo [obor názvů](../../cpp/namespaces-cpp.md) nemůže mít identifikátor GUID.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Příklad

Následující ukázka kódu generuje C4917:

```cpp
// C4917.cpp
// compile with: /W1
#pragma warning(default : 4917)
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S
{
} s;   // C4917, don't put uuid on a struct

int main()
{
}
```
