---
title: Úložiště bitových polí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f223ff90517b6365645a861420ebe1985f994d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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