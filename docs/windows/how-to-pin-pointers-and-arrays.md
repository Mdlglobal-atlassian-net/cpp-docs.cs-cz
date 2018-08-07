---
title: 'Postupy: Připnutí ukazatelů a polí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba13f3d561b4f7bbd57a7678fcfbea26e09a9984
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569372"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Postupy: Připnutí ukazatelů a polí
Připnutí dílčí objekt definovaný v spravovaný objekt má za následek Připnutí celý objekt.  Například pokud je připnutý libovolný prvek pole, pak celé pole je také připnout. Nejsou žádná rozšíření jazyka pro deklarování připnuté pole. Chcete-li připnout pole, deklarujte ukazatel Připnutí a jeho typ elementu, Připne jeden z jeho prvků.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```cpp  
// pin_ptr_array.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
int main() {  
   array<Byte>^ arr = gcnew array<Byte>(4);  
   arr[0] = 'C';  
   arr[1] = '+';  
   arr[2] = '+';  
   arr[3] = '\0';  
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned  
   unsigned char * cp = p;  
  
   printf_s("%s\n", cp); // bytes pointed at by cp  
                         // will not move during call  
}  
```  
  
### <a name="output"></a>Výstup  
  
```Output  
++  
```  
  
## <a name="see-also"></a>Viz také  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)