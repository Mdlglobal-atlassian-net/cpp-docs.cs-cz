---
title: _mm_cvtsi64x_ss | Microsoft Docs
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
ms.openlocfilehash: 8bb529e8aab204df85de2da0a2fdf4c820964239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340603"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Konkrétní Microsoft**  
  
 Generuje [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] rozšířenou verzi převést 64bitovou celočíselnou hodnotu na hodnotu Floating-Point jednoduchou přesností skalárních (`cvtsi2ss`) instrukcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `a`  
 `__m128` Struktura obsahující čtyři hodnoty s plovoucí desetinnou čárkou jednoduchou přesností.  
  
 [v] `b`  
 64bitové celé číslo má být převeden na hodnotu s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 `__m128` Struktura, jehož první hodnota s plovoucí desetinnou čárkou je výsledek převodu. Ostatní tři hodnoty se zkopírují neliší od `a`.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `__m128` Struktura představuje registraci XMM, takže tento vnitřní umožňuje hodnotu `b` z systémové paměti se přesune do XMM zaregistrovat.  
  
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
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__m128](../cpp/m128.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)