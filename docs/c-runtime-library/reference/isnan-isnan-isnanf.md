---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a0cc60fb80f8d5b78ec2947a87fde82a536b413c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953768"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan, _isnan, _isnanf

Testuje, zda hodnota s plovoucí desetinnou čárkou není číslo (NAN).

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
Hodnota s plovoucí desetinnou čárkou, která má být testována.

## <a name="return-value"></a>Návratová hodnota

V jazyce C **isNaN** makro a funkce **_isnan** a **_isnanf** vrátí nenulovou hodnotu, pokud je argument *x* NaN; v opačném případě vrátí 0.

V C++, funkce šablony **isNaN** vrací **hodnotu true** , pokud je argument *x* NaN; v opačném případě vrátí **hodnotu false**.

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že hodnota NaN nerovná žádné jiné hodnotě NaN, je nutné použít jednu z těchto funkcí nebo makra ke zjištění jedné. Hodnota NaN je generována, pokud výsledek operace s plovoucí desetinnou čárkou nemůže být reprezentován ve formátu s plovoucí desetinnou čárkou IEEE-754 pro zadaný typ. Informace o způsobu reprezentace NaN pro výstup naleznete v tématu [printf](printf-printf-l-wprintf-wprintf-l.md).

Při kompilování C++jako není definováno makro **isNaN** a namísto toho je definována funkce šablony **isNaN** . Chová se stejným způsobem jako makro, ale vrací hodnotu typu **bool** namísto celého čísla.

Funkce **_isnan** a **_isnanf** jsou specifické pro společnost Microsoft. Funkce **_isnanf** je k dispozici pouze v případě, že je zkompilována pro platformu x64.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**, **_isnanf**|\<Math. h >|\<Math. h > nebo \<cmath >|
|**_isnan**|\<float. h >|\<float. h > nebo \<cfloat >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
