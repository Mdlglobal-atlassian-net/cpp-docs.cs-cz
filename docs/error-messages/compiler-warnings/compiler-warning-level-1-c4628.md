---
title: Upozornění (úroveň 1) C4628 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4628
dev_langs:
- C++
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36b3f7e65a6235b7eb890cf1265b949760f370ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082557"
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