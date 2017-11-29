---
title: "Kompilátoru (úroveň 1) upozornění C4165 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4165
dev_langs: C++
helpviewer_keywords: C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b0764442e4a9b920cf120c82715368bcba5c8099
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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