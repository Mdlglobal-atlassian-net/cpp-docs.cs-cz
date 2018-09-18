---
title: Chyba kompilátoru C3383 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e35aa05dd037c7d8a5dfd9f7e8328f3644b901e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109389"
---
# <a name="compiler-error-c3383"></a>Chyba kompilátoru C3383

operator new není podporovaná s/clr: safe

Výstupní soubor **/CLR: safe** kompilace je soubor, který je prokazatelně typově bezpečný a ukazatele nejsou podporovány.

Další informace najdete v tématu,

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Příklad

Následující ukázka generuje C3383.

```
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```