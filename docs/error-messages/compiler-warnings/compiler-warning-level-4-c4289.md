---
title: Upozornění (úroveň 4) C4289 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4289
dev_langs:
- C++
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35cb22c767c0ea64a1536bd4d02ad8653bb94250
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102837"
---
# <a name="compiler-warning-level-4-c4289"></a>Kompilátor upozornění (úroveň 4) C4289

používá nestandardní rozšíření: 'var': řídicí proměnná smyčky deklarovaná ve smyčce For je použita mimo rozsah smyčky For

Při kompilaci s [/Ze](../../build/reference/za-ze-disable-language-extensions.md) a **/Zc:forScope-**, proměnná deklarovaná ve [pro](../../cpp/for-statement-cpp.md) smyčky byl použit po **pro**-oboru smyčky.

Zobrazit [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informace o tom, jak určit standardní chování v **pro** smyčky s **/Ze**.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4289:

```
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```