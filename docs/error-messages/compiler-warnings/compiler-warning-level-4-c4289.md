---
title: Kompilátor upozornění (úroveň 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: 3a997af466ddfdaaf4631afeb53d917ce0338c3b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400900"
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