---
title: Upozornění (úroveň 4) C4062 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4062
dev_langs:
- C++
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9632c6b6259d67a8c3ad02f39dc5e61425550e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114849"
---
# <a name="compiler-warning-level-4-c4062"></a>Kompilátor upozornění (úroveň 4) C4062

'identifier' výčtu v přepnutí výčtu 'enumeration' není zpracován.

Výčet nemá žádná přidružená obslužná rutina `switch` příkaz a neexistuje žádná **výchozí** popisek.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4062:

```
// C4062.cpp
// compile with: /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
      break;   // no default label
   }   // C4062, enumerate 'c' not handled
}

int main() {
}
```