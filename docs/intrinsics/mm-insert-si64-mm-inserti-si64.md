---
title: _mm_insert_si64, _mm_inserti_si64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
dev_langs:
- C++
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc85f56660702afe1c05f3626b3b28b0b566dbd5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64
**Microsoft Specific**  
  
 Generuje `insertq` instrukce vložit bits z jeho Druhý operand do své první operand.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__m128i _mm_insert_si64(  
   __m128i Source1,  
   __m128i Source2  
);  
__m128i _mm_inserti_si64(  
   __m128i Source1,  
   __m128i Source2  
   int Length,  
   int Index  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Source1`  
 Pole 128-bit s vstupní data v jeho nižší 64bitová verze, do kterých se vloží pole.  
  
 [in]  `Source2`  
 Pole 128-bit s data k vložení v jeho nízkou bits.  Pro `_mm_insert_si64`, také obsahuje pole popisovač v jeho vysokou bits.  
  
 [in]  `Length`  
 Celočíselná konstanta, který určuje pole, které chcete vložit.  
  
 [in]  `Index`  
 Celočíselná konstanta, který určuje index nejméně významný bit pole, do kterého se budou vkládat data.  
  
## <a name="return-value"></a>Návratová hodnota  
 128-bit pole, jejichž nižší 64bitová verze obsahovat původní nízkou 64bitová verze systému `Source1` s polem zadaný bit nahrazuje nízkou bity `Source2`. Horní 64bitová verze vrácené hodnoty nejsou definovány.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_mm_insert_si64`|SSE4a|  
|`_mm_inserti_si64`|SSE4a|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tento vnitřní vygeneruje `insertq` pokyn k vložení bits z `Source2` do `Source1`. Existují dvě verze tohoto vnitřní: `_mm_inserti_si64`, je okamžitou verze a `_mm_insert_si64` je ten, který není okamžitý.  Každá verze extrahuje bitové pole dané délky z zdroj2 a vloží je do zdroj1.  Extrahované bits jsou nejméně významný bity zdroj2.  Délka a index jeho nejméně významný bit je definována zdroj1 pole, do kterého budou vloženy tyto služby bits.  Hodnot délkou a index, která mod 64, proto se jako 63 interpretují -1 do 127. Pokud součet (snížené) bit indexu a délky (snížené) pole je větší než 64, není definován výsledky. Hodnota 0 pro délka pole interpretována jako 64.  Pokud jsou oba nulové, služba bits 63:0 z index délku a bitová pole `Source2` jsou vloženy do `Source1`.  Pokud bit index je nulová délka pole je nulová. však není definován výsledky.  
  
 Ve volání _mm_insert_si64 délka pole je součástí služby bits 77:72 zdroj2 a index v bits 69:64.  
  
 Když zavoláte `_mm_inserti_si64` s argumenty, kompilátor nemůže určit být konstanty typu integer, kompilátor generuje kód do registraci XMM pack tyto hodnoty a volání `_mm_insert_si64`.  
  
 K určení podporu hardwaru pro `insertq` instrukce volání `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 `CPUInfo[2] (ECX)`. Tato verze bude 1, pokud je podporováno pokyn a 0 jinak. Pokud jste spustili kód, který používá tento vnitřní hardware, který nepodporuje `insertq` instrukce, nepředvídatelné výsledky.  
  
## <a name="example"></a>Příklad  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source1, source2, source3, result1, result2, result3;  
  
int  
main()  
{  
  
    __int64 mask;  
  
    source1.ui64[0] = 0xffffffffffffffffll;  
    source2.ui64[0] = 0xfedcba9876543210ll;  
    source2.ui64[1] = 0xc10;  
    source3.ui64[0] = source2.ui64[0];  
  
    result1.m = _mm_insert_si64 (source1.m, source2.m);  
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);  
    mask = 0xffff << 12;  
    mask = ~mask;  
    result3.ui64[0] = (source1.ui64[0] & mask) |  
                      ((source2.ui64[0] & 0xffff) << 12);  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
  
}  
```  
  
```Output  
result1 = 0xfffffffff3210fff  
result2 = 0xfffffffff3210fff  
result3 = 0xfffffffff3210fff  
```  
  
**Konkrétní Microsoft END**  
 Copyright 2007 pokročilé Micro zařízení, Inc. Všechna práva vyhrazena. Opakuje se svolením Advanced Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)