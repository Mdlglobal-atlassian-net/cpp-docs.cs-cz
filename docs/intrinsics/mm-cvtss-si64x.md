---
title: _mm_cvtss_si64x | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtss_si64x
dev_langs:
- C++
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 665c52fc0dd0645e25d3014cc28f9fdfba344e2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x
**Konkrétní Microsoft**  
  
 Generuje [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] rozšířenou verzi převést skalární hodnota jednoho přesnost číslo s plovoucí desetinnou na 64bitové celé číslo (`cvtss2si`) instrukcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `value`  
 `__m128` Struktura obsahující hodnot s plovoucí čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 64bitové celočíselné výsledek převodu první hodnota s plovoucí desetinnou čárkou na celé číslo.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 První prvek hodnoty strukturu je převést na celé číslo a vrácena. Zaokrouhlení ovládací bity v MXCSR slouží k určení chování zaokrouhlení. Výchozí režim zaokrouhlení se zaokrouhlí na nejbližší zaokrouhlení na sudé číslo. Pokud je 0,5 v části decimal. Protože `__m128` struktura reprezentuje XMM registrace, trvá Tento vnitřní hodnotu z registru XMM a zapíše ho do systémové paměti.  
  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
## <a name="example"></a>Příklad  
  
```  
// _mm_cvtss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] =  
                           { 101.25, 200.75, 300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvtss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__m128d](../cpp/m128d.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)