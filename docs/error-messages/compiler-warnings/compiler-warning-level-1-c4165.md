---
title: Upozornění kompilátoru (úroveň 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: bb036f7672a074e859d3e19083e256bd80c93578
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176093"
---
# <a name="compiler-warning-level-1-c4165"></a>Upozornění kompilátoru (úroveň 1) C4165

Hodnota HRESULT se převádí na bool; Opravdu to chcete?

Při použití HRESULT v příkazu [if](../../cpp/if-else-statement-cpp.md) se hodnota HRESULT převede na [bool](../../cpp/bool-cpp.md) , pokud explicitně netestujete proměnnou jako HRESULT. Toto upozornění je ve výchozím nastavení vypnuté.

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
