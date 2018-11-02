---
title: Kompilátor upozornění (úroveň 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: d8769f5663ca0bde9048e52d4579012dfccab0a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532025"
---
# <a name="compiler-warning-level-1-c4288"></a>Kompilátor upozornění (úroveň 1) C4288

používá se nestandardní rozšíření: 'var': Proměnná ovládacího prvku smyčky deklarovaná ve smyčce for-loop se používá mimo obor smyčky for loop; je v konfliktu s deklarací ve vnějším oboru.

Při kompilaci s [/Ze](../../build/reference/za-ze-disable-language-extensions.md) a **/Zc:forscope-**, proměnná deklarovaná ve **pro** smyčky byl použit po [pro](../../cpp/for-statement-cpp.md)-oboru smyčky. Rozšíření společnosti Microsoft pro jazyk C++ umožňuje tato proměnná zůstane v oboru a C4288 upozorňuje, že první deklarace proměnné se nepoužívá.

Zobrazit [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informace o tom, jak zadat rozšíření společnosti Microsoft v **pro** smyčky s /Ze.

Následující ukázka generuje C4288:

```
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```