---
title: Upozornění (úroveň 1) C4288 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8b9e82f8cb24c4635fb64c3ac0a1c82e301c086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056482"
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