---
title: _BitScanForward _BitScanForward64 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
dev_langs:
- C++
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e563e7240c1797bf863ee0762f923e91a6f05bb0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699882"
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward, _BitScanForward64
**Specifické pro Microsoft**  
  
 Hledat maskování dat z nejméně významných bitů (LSB) na nejvýznamnější bit (MSB) nastaveného bitu (1).  
  
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
*Index*<br/>
[out] Načtená verze umístění prvního nastaveného bitu (1) nalezena.  
  
*Maska*<br/>
[in] 32bitové nebo 64bitové hodnotu vyhledávání.  
  
## <a name="return-value"></a>Návratová hodnota  
 0, pokud maska je nula. nenulový jinak.  
  
## <a name="remarks"></a>Poznámky  
 Pokud nastaveného bitu nenajde, vrátí se bit umístění prvního nastaveného bitu nalezen v prvním parametru. Pokud se nenajde žádný nastaveného bitu, je vrácena 0. v opačném případě vrátí hodnotu 1.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`_BitScanForward`|x86, ARM, x64|  
|`_BitScanForward64`|ARM, x64|  
  
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
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)