---
title: Kompilátor upozornění (úroveň 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: ebb71155774ce32d6b4fc2b9920fdd31dd466841
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466021"
---
# <a name="compiler-warning-level-1-c4628"></a>Kompilátor upozornění (úroveň 1) C4628

spřežky nejsou podporovány se -Ze. Sekvence znaků 'digraph' není interpretována jako alternativní token pro 'char'.

Digraphy nejsou podporované v rámci [/Ze](../../build/reference/za-ze-disable-language-extensions.md). Toto upozornění bude následovat chyba.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4628:

```
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```