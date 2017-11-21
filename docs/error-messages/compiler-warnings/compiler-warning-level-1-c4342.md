---
title: "Kompilátoru (úroveň 1) upozornění C4342 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4342
dev_langs: C++
helpviewer_keywords: C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: faea23fcfa1e323ec28d81aa5abeb27f3c87cef1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4342"></a>C4342 kompilátoru upozornění (úroveň 1)
Změna v chování: '*funkce*se volá, ale byla zavolána operátor členů v předchozích verzích  
  
 Ve verzích Visual C++ před Visual Studio 2002 členem byla volána, ale toto chování se změnil a kompilátor teď vyhledá nejlepší shodu v oboru názvů.  
  
 Pokud byl nalezen operátor členů, kompilátor nebude dříve zvažte obor názvů operátory oboru. Pokud je lepší shodu v oboru názvů, aktuální kompilátor správně volá, zatímco předchozí kompilátory nebude považuje.  
  
 Toto upozornění je třeba zakázat po úspěšně portu kódu na aktuální verzi.  Kompilátor může poskytnout falešně pozitivních zjištění generování toto upozornění pro kód tam, kde není žádná změna v chování.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Následující ukázka generuje C4342:  
  
```cpp  
// C4342.cpp  
// compile with: /EHsc /W1  
#include <fstream>  
#pragma warning(default: 4342)  
using namespace std;  
struct X : public ofstream {  
   X();  
};  
  
X::X() {  
   open( "ofs_bug_ev.txt." );  
   if ( is_open() ) {  
      *this << "Text" << "<-should be text" << endl;   // C4342  
      *this << ' ' << "<-should be space symbol" << endl;   // C4342  
   }  
}  
  
int main() {  
   X b;  
   b << "Text" << "<-should be text" << endl;  
   b << ' ' << "<-should be space symbol" << endl;  
}  
```