---
title: asin, asinf, asinl
ms.date: 04/05/2018
apiname:
- asinf
- asinl
- asin
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 20a2ffc37ea666207b9558cb5c282c414cfd4838
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476043"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Vypočítá arkussinus.

## <a name="syntax"></a>Syntaxe

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, jejíž Arkus kosinus je vypočítán.

## <a name="return-value"></a>Návratová hodnota

**Asin** funkce vrátí hodnotu Arkus sinus (inverzní sinus funkce) z *x* v rozsahu - pí/2 do pí/2 radiánů.

Ve výchozím nastavení pokud *x* je menší než -1 nebo větší než 1, **asin** vrátí nekonečno.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**NEPLATNÝ**|**_DOMÉNA**|
|ROZMEZÍ **QNAN**, **AJÍT**|žádná|**_DOMÉNA**|
|&#124;x&#124;>1|**NEPLATNÝ**|**_DOMÉNA**|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **asin** s **float** a **dlouhé** **double** hodnoty. V programu jazyka C **asin** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf –**, **asinl –**|\<Math.h >|\<cmath > nebo \<math.h >|

## <a name="example"></a>Příklad

Další informace najdete v tématu [acos, acosf –, acosl –](acos-acosf-acosl.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[Cos cosf –, cosl –](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
