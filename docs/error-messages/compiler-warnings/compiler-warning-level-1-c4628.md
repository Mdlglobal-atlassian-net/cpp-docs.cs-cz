---
title: Upozornění kompilátoru (úroveň 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: affb2b5231d3745d4826e92657e355ec99570e7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199664"
---
# <a name="compiler-warning-level-1-c4628"></a>Upozornění kompilátoru (úroveň 1) C4628

spřežky nejsou podporovány se -Ze. Sekvence znaků 'digraph' není interpretována jako alternativní token pro 'char'.

V rámci [/ze](../../build/reference/za-ze-disable-language-extensions.md)nejsou podporovány grafy. Toto upozornění bude následováno chybou.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4628:

```cpp
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```
