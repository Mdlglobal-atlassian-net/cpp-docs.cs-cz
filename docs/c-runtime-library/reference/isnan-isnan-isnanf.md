---
title: isNaN – _isnan –, _isnanf
ms.date: 01/31/2019
apiname:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: 8a907dd33803cebd7bc5d71789834d115333b6a0
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703087"
---
# <a name="isnan-isnan-isnanf"></a>isNaN – _isnan –, _isnanf

Testuje, zda je hodnota s plovoucí desetinnou čárkou není číslo (NAN).

## <a name="syntax"></a>Syntaxe

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

V jazyce C **isNaN –** – makro a **_isnan –** a **_isnanf** funkce vrátí nenulovou hodnotu, pokud argument *x* je NAN; jinak vrátí hodnotu, Vrátí 0.

V jazyce C++ **isNaN –** funkce šablony vrátí **true** Pokud argument *x* je NaN; v opačném případě vrátí **false**.

## <a name="remarks"></a>Poznámky

Protože hodnota NaN není výsledkem porovnání jako jakákoli jiná hodnota NaN, musíte použít některý z těchto funkcí nebo makra rozpoznat jeden. NaN se vygeneruje, když ve formátu s plovoucí desetinnou čárkou IEEE 754 pro zadaný typ nelze reprezentovat výsledek operace s plovoucí desetinnou čárkou. Informace o tom, jak je reprezentovaná NaN pro výstup, naleznete v tématu [printf](printf-printf-l-wprintf-wprintf-l.md).

Při kompilaci jako C++, **isnan** makro není definované a **isnan** místo toho je definována šablona funkce. Jak se bude chovat stejně jako makra, ale vrátí hodnotu typu **bool** namísto celého čísla.

**_Isnan –** a **_isnanf** funkce jsou specifické pro společnost Microsoft. **_Isnanf** funkce dostupná jenom při kompilaci pro x64.

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**, **_isnanf**|\<math.h>|\<Math.h > nebo \<cmath >|
|**_isnan**|\<float.h >|\<float.h > nebo \<cfloat – >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf –](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
