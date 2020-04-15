---
title: asin, asinf, asinl
ms.date: 4/2/2020
api_name:
- asinf
- asinl
- asin
- _o_asin
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 424fee6995fae4a7f878054ede1bb85d33d1706d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334133"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Vypočítá arcinin.

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

*X*<br/>
Hodnota, jejíž arcsin se má vypočítat.

## <a name="return-value"></a>Návratová hodnota

Funkce **asin** vrátí arcsin (inverzní sinusovou funkci) *x* v rozsahu -π/2 až π/2 radiánů.

Ve výchozím nastavení, pokud *x* je menší než -1 nebo větší než 1, **asin** vrátí neurčitý.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**Neplatný**|**_DOMAIN**|
|± **QNAN**, **IND**|Žádná|**_DOMAIN**|
|&#124;x&#124;>1|**Neplatný**|**_DOMAIN**|

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje přetížení, můžete volat přetížení **asin** s **float** a **dlouhé** **dvojité** hodnoty. V programu C **asin** vždy trvá a vrací **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinná hlavička (C)|Povinné záhlaví (C++)|
|-------------|---------------------|-|
|**asin**, **asinf**, **asinl**|\<math.h>|\<cmath> \<nebo math.h>|

## <a name="example"></a>Příklad

Další informace naleznete [v tématu acos, acosf, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
