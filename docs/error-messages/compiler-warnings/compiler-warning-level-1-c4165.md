---
title: Kompilátoru (úroveň 1) upozornění C4165 | Microsoft Docs
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
ms.openlocfilehash: 39487999f2aa74a5600d84d71917712e03b2d626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277563"
---
# <a name="compiler-warning-level-1-c4165"></a>C4165 kompilátoru upozornění (úroveň 1)
"HRESULT" je převáděn na 'bool'; jste si jistí, že je to, co chcete použít?  
  
Při použití HRESULT v [Pokud](../../cpp/if-else-statement-cpp.md) příkaz, hodnota HRESULT text bude převeden na [bool](../../cpp/bool-cpp.md) Pokud testujete explicitně pro proměnnou jako HRESULT. Toto upozornění je ve výchozím nastavení vypnutý.  
  
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