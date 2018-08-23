---
title: _mm_cvttss_si64x | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvttss_si64x
dev_langs:
- C++
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f70588ca17a2bde34de6a16b62b18fa6125b08c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464848"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x
**Specifické pro Microsoft**  
  
 Vysílá x64 rozšířenou verzi Convert s číslem plovoucí desetinné čárky jednoduchou přesnost zkrácení na 64bitové celé číslo (`cvttss2si`) instrukce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `value`  
 `__m128` Struktury obsahující hodnoty s plovoucí desetinnou čárkou jednoduchou přesností.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výsledek převodu první hodnota s plovoucí desetinnou čárkou na 64bitové celé číslo.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`_mm_cvttss_si64x`|x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Vnitřní typy se liší od `_mm_cvtss_si64x` pouze v tom, že se zkrátí nepřesné převody směrem k nule. Vzhledem k tomu, `__m128` struktura představuje registru XMM, vygeneruje instrukce přesouvá data z registru XMM do systémové paměti.  
  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
## <a name="example"></a>Příklad  
  
```  
// _mm_cvttss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvttss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] = { 101.5, 200.75,  
                                          300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvttss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__m128](../cpp/m128.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)