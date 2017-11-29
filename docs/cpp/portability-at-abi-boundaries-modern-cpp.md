---
title: "Přenositelnost u rozhraní ABI (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 397c3faeeed85633f949c331c9be12c6a8a5a46b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Přenositelnost u rozhraní ABI (moderní verze jazyka C++)
Použití dostatečně přenosné typy a pravidla týkající se na binární rozhraní hranice. "Přenosné type" je předdefinovaný typ C nebo struktura, která obsahuje jenom vestavěné typy C. Typy tříd lze použít pouze když volající a volaný dohodnou na rozložení, volání konvence atd. To je možné pouze, pokud jsou obě kompilovat s stejné kompilátoru a nastavení kompilátoru.  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>Postup vyrovnání třídu pro přenositelnost jazyka C  
 Když volající může kompilovat s jinou kompilátoru/jazyk a potom "zploštění" k **extern "C"** rozhraní API pomocí konkrétní konvence volání:  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern "C" {        // functions using explicit "this"  
   struct widget;   // opaque type (forward declaration only)  
   widget* STDCALL widget_create();      // constructor creates new "this"  
   void STDCALL widget_destroy(widget*); // destructor consumes "this"  
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)