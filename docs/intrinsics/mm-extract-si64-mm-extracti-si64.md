---
title: _mm_extract_si64 _mm_extracti_si64 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
dev_langs:
- C++
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d4db2fa67924a6925a19d2714c604f2c9aaa4e7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705650"
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64, _mm_extracti_si64

**Specifické pro Microsoft**  
  
Generuje `extrq` instrukce k extrakci zadané bitů z nízké 64 bitů svůj první argument.  
  
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
*Zdroj*<br/>
[in] 128bitové pole se vstupní data v dolním 64 bitů.  
  
*Popisovač*<br/>
[in] Pole 128-bit, který popisuje bitové pole k extrakci.  
  
*Délka*<br/>
[in] Celé číslo, které určuje délku pole, které chcete extrahovat.  
  
*Index*<br/>
[in] Celé číslo, které určuje index pole k extrahování  
  
## <a name="return-value"></a>Návratová hodnota  
 128bitové pole s polem extrahované v její nejméně významných bitů.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tomto vnitřní vygeneruje `extrq` instrukce k extrakci bitů z `Source`. Existují dvě verze tohoto vnitřní: `_mm_extracti_si64` okamžité verze a `_mm_extract_si64` je – okamžitě.  Každá verze extrahuje ze `Source` bitového pole definované jeho délky a index jeho nejméně významných bitů. Index a délka hodnoty pocházejí mod 64, tedy -1 do 127 číslic se interpretují jako 63. Pokud součet (nižší) index a délky pole (nižší) je větší než 64, nejsou výsledky definovány. Hodnota 0 pro délku pole je interpretován jako 64. Pokud je index délku a bitová pole jsou obě nulové, služba bits 63:0 z `Source` jsou extrahovány. Pokud délka pole je nula, ale bit index je nenulová, nejsou výsledky definovány.  
  
 Ve volání _mm_extract_si64 `Descriptor` obsahuje index v 13:8 bitů a délku pole dat extrahovaným bits 5:0..  
  
 Při volání `_mm_extracti_si64` argumentů, kompilátor nemůže určit být konstanty typu integer kompilátor generuje kód se zabalit tyto hodnoty do registru XMM (`Descriptor`) a k volání `_mm_extract_si64`.  
  
 K určení hardwarovou podporu `extrq` instrukce, volání `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolujte bit 6 `CPUInfo[2] (ECX)`. Tato verze bude 1, pokud podporované instrukce a 0 jinak. Pokud je třeba spustit kód, který používá tento vnitřní hardware, který nepodporuje `extrq` instrukce, výsledky nepředvídatelné.  
  
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
  
**Specifické pro END Microsoft**

Copyright 2007 pokročilé zařízení Micro, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [_mm_insert_si64, _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)