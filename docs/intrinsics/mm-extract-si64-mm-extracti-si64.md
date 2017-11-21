---
title: _mm_extract_si64 _mm_extracti_si64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
dev_langs: C++
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 33467ac3a4397c3f446abe370dca5dc16c1a92ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64 _mm_extracti_si64
**Konkrétní Microsoft**  
  
 Generuje `extrq` instrukce k extrahování určené bits z nízkou 64 bitů svůj první argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__m128i _mm_extract_si64(  
   __m128i Source,  
   __m128i Descriptor  
);  
__m128i _mm_extracti_si64(  
   __m128i Source,  
   int Length,  
   int Index  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`Source`  
 Pole 128-bit s vstupní data v jeho nižší 64 bitů.  
  
 [v]`Descriptor`  
 Pole 128-bit, který popisuje pole bit k extrakci.  
  
 [v]`Length`  
 Celé číslo, které určuje délka pole k extrakci.  
  
 [v]`Index`  
 Celé číslo, které určuje index pole extrahovat  
  
## <a name="return-value"></a>Návratová hodnota  
 Pole 128-bit s poli extrahované v jeho nejméně významný bits.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tento vnitřní vygeneruje `extrq` instrukce k extrakci bits z `Source`. Existují dvě verze tohoto vnitřní: `_mm_extracti_si64` je okamžitou verze a `_mm_extract_si64` je ten, který není okamžitý.  Každá verze extrahuje z `Source` bitové pole definované jeho délky a index jeho nejméně významný bit. Hodnot délkou a index, která mod 64, proto se jako 63 interpretují -1 do 127. Pokud součet (snížené) indexu a délky (snížené) pole je větší než 64, není definován výsledky. Hodnota 0 pro délka pole interpretována jako 64. Pokud jsou oba nulové, služba bits 63:0 z index délku a bitová pole `Source` extrahují. Pokud bit index je nulová délka pole je nulová. však není definován výsledky.  
  
 Ve volání _mm_extract_si64 `Descriptor` obsahuje index v 13:8 bitů a délky pole dat extrahovat v bits 5:0...  
  
 Když zavoláte `_mm_extracti_si64` s argumenty, nemůže být konstanty typu integer zjistit kompilátor kompilátor generuje kód do pack tyto hodnoty do registraci XMM (`Descriptor`) a k volání `_mm_extract_si64`.  
  
 K určení podporu hardwaru pro `extrq` instrukce, volání `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 `CPUInfo[2] (ECX)`. Tato verze bude 1, pokud je podporováno pokyn a 0 jinak. Pokud spustíte kód, který používá tento vnitřní hardware, který nepodporuje `extrq` instrukce, nepředvídatelné výsledky.  
  
## <a name="example"></a>Příklad  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source, descriptor, result1, result2, result3;  
  
int  
main()  
{  
    source.ui64[0] =     0xfedcba9876543210ll;  
    descriptor.ui64[0] = 0x0000000000000b1bll;  
  
    result1.m = _mm_extract_si64 (source.m, descriptor.m);  
    result2.m = _mm_extracti_si64(source.m, 27, 11);  
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
}  
```  
  
```Output  
result1 = 0x30eca86  
result2 = 0x30eca86  
result3 = 0x30eca86  
```  
  
**Konkrétní Microsoft END**  
 Copyright 2007 pokročilé Micro zařízení, Inc. Všechna práva vyhrazena. Opakuje se svolením Advanced Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [_mm_insert_si64 _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)