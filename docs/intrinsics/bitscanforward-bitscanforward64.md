---
title: _BitScanForward _BitScanForward64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
dev_langs: C++
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 94fe30e65cc501e16fe31bd04b5cb786a323ccdb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward _BitScanForward64
**Konkrétní Microsoft**  
  
 Vyhledávání dat maska z nejméně významný bit (LSB) na nejvyšší bit (MSB) pro verzi sady (1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char _BitScanForward(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanForward64(  
   unsigned long * Index,  
   unsigned __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`Index`  
 Načtená bit pozice první nastavit chvíli (1) nalezena.  
  
 [v]`Mask`  
 32bitovou nebo 64bitovou hodnotu k vyhledání.  
  
## <a name="return-value"></a>Návratová hodnota  
 0, pokud maska je nula. nenulové hodnoty v opačném případě.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je nalezen bit sadu, vrátí se pozice bit první sada bit najít v první parametr. Pokud se nenajde žádný sadu bit, je vrácena 0; jinak vrátí hodnotu 1.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_BitScanForward`|x86 ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_BitScanForward64`|ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="example"></a>Příklad  
  
```  
// BitScanForward.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanForward)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanForward(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## <a name="input"></a>Vstup  
  
```  
12  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 2  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)