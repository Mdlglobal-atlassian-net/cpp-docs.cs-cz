---
title: "Postupy: Připnutí ukazatelů a polí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 02c0f42042f5cdda0898e7d2c74754e68fb67113
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-pin-pointers-and-arrays"></a>Postupy: Připnutí ukazatelů a polí
Připnutí dílčí objekt definovaný v spravovaného objektu má za následek Připnutí celý objekt.  Například pokud je připnutý libovolný element pole, pak celé pole je také připojena. Neexistují žádné rozšíření pro jazyk pro deklarování definovaného pole. Chcete-li připnout pole, deklarujte Připnutí ukazatel na jeho typ elementu a kód pin, jeden z jejích elementů.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```  
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
  
```  
++  
```  
  
## <a name="see-also"></a>Viz také  
 [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md)