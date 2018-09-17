---
title: _BitScanReverse _BitScanReverse64 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
dev_langs:
- C++
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab174484cb305e26c23d1c1d6b5e573341c9035c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716961"
---
# <a name="bitscanreverse-bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64
**Specifické pro Microsoft**  
  
 Hledat maskování dat od nejvýznamnější bit (MSB) na nejméně významných bitů (LSB) u nastaveného bitu (1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char _BitScanReverse(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanReverse64(  
   unsigned long * Index,  
   unsigned __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Index*<br/>
[out] Načtená verze umístění prvního nastaveného bitu (1) nalezena.  
  
*Maska*<br/>
[in] 32bitové nebo 64bitové hodnotu vyhledávání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu, pokud `Index` byl sady, nebo 0, pokud nebyly nalezeny žádné sady bitů.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`_BitScanReverse`|x86, ARM, x64|\<intrin.h >|  
|`_BitScanReverse64`|ARM, x64||  
  
## <a name="example"></a>Příklad  
  
```  
// BitScanReverse.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanReverse)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanReverse(&index, mask);  
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
Mask: 12 Index: 3  
```  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)