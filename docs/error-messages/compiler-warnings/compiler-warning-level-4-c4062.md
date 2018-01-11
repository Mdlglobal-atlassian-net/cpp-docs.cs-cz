---
title: "Kompilátoru (úroveň 4) upozornění C4062 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4062
dev_langs: C++
helpviewer_keywords: C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e346b671422f6b2708e625b0a7d0a453c4524cdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4062"></a>C4062 kompilátoru upozornění (úroveň 4)
nejsou zpracovávány enumerátor "identifikátor" v přepínači výčtu 'výčtu.  
  
 Výčet nemá žádné přidruženou obslužnou rutinu v `switch` příkaz a neexistuje žádná **výchozí** popisek.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4062:  
  
```  
// C4062.cpp  
// compile with: /W4  
#pragma warning(default : 4062)  
enum E { a, b, c };  
void func ( E e ) {  
   switch(e) {  
      case a:  
      case b:  
      break;   // no default label  
   }   // C4062, enumerate 'c' not handled  
}  
  
int main() {  
}  
```