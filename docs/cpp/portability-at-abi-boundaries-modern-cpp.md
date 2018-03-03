---
title: "Přenositelnost u rozhraní ABI (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 06cb6c97580b4c4c9a6c961cb76f2c4d84d841ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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