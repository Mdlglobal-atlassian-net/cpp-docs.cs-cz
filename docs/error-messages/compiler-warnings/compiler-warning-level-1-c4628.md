---
title: Upozornění kompilátoru (úroveň 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: 6063755db5ac517d868bc47d2c417356ccef5d58
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051433"
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