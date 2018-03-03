---
title: "Úložiště bitových polí | Microsoft Docs"
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
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1be04ba4c68b2629a5e765788af95a203ae06b34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-bit-fields"></a>Úložiště bitových polí
**ANSI 3.5.2.1** pořadí přidělení bitových polí v rámci typ int  
  
 Bitová pole jsou přidělené v rámci celé číslo z nejméně významným na většinu významných bitů. V následujícím kódu  
  
```  
struct mybitfields  
{  
   unsigned a : 4;  
   unsigned b : 5;  
   unsigned c : 7;  
} test;  
  
int main( void )  
{  
   test.a = 2;  
   test.b = 31;  
   test.c = 0;  
}  
```  
  
 službu bits by být uspořádána následujícím způsobem:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 Jelikož procesory 80x86 ukládají nižší bajt celočíselných hodnot před vyšší bajt, bude celé číslo 0x01F2 ve fyzické paměti uloženo jako 0xF2 následované 0x01.  
  
## <a name="see-also"></a>Viz také  
 [Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)