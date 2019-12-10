---
title: Upozornění kompilátoru (úroveň 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: b9083670465d68493d90a8e96ff7ee5db34c1978
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991321"
---
# <a name="compiler-warning-level-4-c4289"></a>Upozornění kompilátoru (úroveň 4) C4289

používá nestandardní rozšíření: 'var': řídicí proměnná smyčky deklarovaná ve smyčce For je použita mimo rozsah smyčky For

Při kompilaci s [/ze](../../build/reference/za-ze-disable-language-extensions.md) a **/Zc: forScope-** byla jako rozsah smyčky **for-Loop**použita Proměnná deklarovaná ve smyčce [for](../../cpp/for-statement-cpp.md) .

Viz [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) pro informace o **tom, jak** určit standardní chování ve smyčkách s **/ze**.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Následující ukázka generuje C4289:

```cpp
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```
