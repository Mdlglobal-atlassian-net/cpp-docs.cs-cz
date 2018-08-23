---
title: _mm_cvtsi64x_ss | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtsi64x_ss
dev_langs:
- C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae300569c4aa04a313f44a23fe988f1de7b826a1
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465487"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Specifické pro Microsoft**  
  
 Generuje x64 rozšířenou verzi převést 64bitové celé číslo na skalární hodnotu plovoucí desetinné čárky jednoduchou přesnost (`cvtsi2ss`) instrukce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `a`  
 `__m128` Struktury obsahující čtyři hodnoty s plovoucí desetinnou čárkou jednoduchou přesností.  
  
 [in] `b`  
 64bitové celé číslo k převedení na hodnotu s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 `__m128` Strukturu, jejíž první hodnota s plovoucí desetinnou čárkou je výsledkem převodu. Tři hodnoty jsou beze změny zkopírují z `a`.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `__m128` Struktura představuje XMM registru, proto tuto vnitřní umožňuje hodnotu `b` ze systémové paměti přesunout do XMM zaregistrovat.  
  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
## <a name="example"></a>Příklad  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
```Output  
54.000000 0.000000 0.000000 0.000000  
```  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__m128](../cpp/m128.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)