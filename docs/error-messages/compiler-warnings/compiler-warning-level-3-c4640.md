---
title: Kompilátoru (úroveň 3) upozornění C4640 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4640
dev_langs:
- C++
helpviewer_keywords:
- C4640
ms.assetid: f76871f6-e436-4c35-9793-d2f22f7e1c7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34c55334b49ac325d23f73e9ceaaa8613ca9c45d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290436"
---
# <a name="compiler-warning-level-3-c4640"></a>C4640 kompilátoru upozornění (úroveň 3)
'instance': vytváření místní statické objektu není bezpečné pro přístup z více vláken  
  
 Statická instance objektu není bezpečné pro přístup z více vláken.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4640:  
  
```  
// C4640.cpp  
// compile with: /W3  
#pragma warning(default:4640)  
  
class X {  
public:  
   X() {  
   }  
};  
  
void f() {  
   static X aX;   // C4640  
}  
  
int main() {  
   f();  
}  
```