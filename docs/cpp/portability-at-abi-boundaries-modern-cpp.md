---
title: Přenositelnost u rozhraní ABI (moderní verze jazyka C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb9ce8012db8617afc7af3183bd7439ddeb8fab7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402348"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Přenositelnost u rozhraní ABI (moderní verze jazyka C++)
Použití dostatečně přenosné typy a pravidla týkající se na binární rozhraní hranice. "Přenosné type" je předdefinovaný typ jazyka C nebo struktura, která obsahuje pouze předdefinované typy jazyka C. Typy tříd jde použít jenom při volajícím a volaným shodnout na rozložení, volání konvence atd. To je možné, pouze když obě jsou kompilovány pomocí stejného kompilátoru a nastavení kompilátoru.  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>Jak sloučit třídy pro přenositelnost jazyka C  
 Když volající může být kompilována s jinou kompilátoru a jazyk a pak "sloučit" k **extern "C"** rozhraní API s konkrétní konvence volání:  
  
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
  
## <a name="see-also"></a>Viz také:  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)