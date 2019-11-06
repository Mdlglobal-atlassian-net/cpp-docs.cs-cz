---
title: Upozornění kompilátoru (úroveň 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: 81094bf019060b56337347f7d364ead7c78c8128
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626663"
---
# <a name="compiler-warning-level-1-c4288"></a>Upozornění kompilátoru (úroveň 1) C4288

používá se nestandardní rozšíření: var: proměnná ovládacího prvku smyčky deklarovaná ve smyčce for-Loop se používá mimo obor smyčky for-Loop; je v konfliktu s deklarací ve vnějším oboru.

Při kompilaci s [/ze](../../build/reference/za-ze-disable-language-extensions.md) a **/Zc: forScope-** byla jako rozsah smyčky [for-Loop](../../cpp/for-statement-cpp.md)použita Proměnná deklarovaná ve smyčce **for** . Rozšíření společnosti Microsoft pro C++ jazyk umožňuje, aby tato proměnná zůstala v rozsahu a C4288 vás, že první deklarace proměnné se nepoužívá.

Informace o tom, jak zadat rozšíření Microsoftu v **pro smyčky for for** with/ze., najdete v tématu [/Zc: forScope.](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)

Následující ukázka generuje C4288:

```cpp
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```