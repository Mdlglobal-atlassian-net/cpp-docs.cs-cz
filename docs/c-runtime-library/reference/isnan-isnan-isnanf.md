---
title: isNaN – _isnan –, _isnanf
ms.date: 04/05/2018
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
ms.openlocfilehash: ce111569b7caee9d0c7b8f35352c395571ad08b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650863"
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

V jazyce C++ **isNaN –** šablony funkce vrátit **true** Pokud argument *x* je NAN; v opačném případě vrátí **false**.

## <a name="remarks"></a>Poznámky

C **isnan** – makro a **_isnan –** a **_isnanf** funkce testování s plovoucí desetinnou čárkou *x*, vrací nenulovou hodnotu, pokud *x* je hodnota číslo (NAN). NAN se vygeneruje, když ve formátu s plovoucí desetinnou čárkou IEEE 754 pro zadaný typ nelze reprezentovat výsledek operace s plovoucí desetinnou čárkou. Informace o tom, jak je reprezentovaná NAN pro výstup, naleznete v tématu [printf](printf-printf-l-wprintf-wprintf-l.md).

Při kompilaci jako C++, **isnan** makro není definované a **isnan** místo toho je definována šablona funkce. Vrátí hodnotu typu **bool** namísto celého čísla.

**_Isnan –** a **_isnanf** funkce jsou specifické pro Microsoft. **_Isnanf** funkce dostupná jenom při kompilaci pro x64.

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|-------------|---------------------------|-------------------------------|
|**isNaN –**, **_isnanf**|\<Math.h >|\<Math.h > nebo \<cmath >|
|**_isnan**|\<float.h >|\<float.h > nebo \<cfloat – >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_finite, _finitef](finite-finitef.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
