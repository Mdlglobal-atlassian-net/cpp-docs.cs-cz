---
title: Upozornění (úroveň 1) C4165 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4165
dev_langs:
- C++
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c532ddee7a2066190c2f926ba7b1240c0418f6c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084923"
---
# <a name="compiler-warning-level-1-c4165"></a>Kompilátor upozornění (úroveň 1) C4165

"HRESULT" je převáděn na 'bool'; jste si jisti, že je to, co chcete?

Při použití HRESULT v [Pokud](../../cpp/if-else-statement-cpp.md) příkaz, hodnota HRESULT se převedou na [bool](../../cpp/bool-cpp.md) Pokud explicitně test pro proměnnou jako HRESULT. Toto upozornění je vypnuto ve výchozím nastavení.

## <a name="example"></a>Příklad

Následující ukázka generuje C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```