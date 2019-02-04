---
title: isfinite, _finite, _finitef
ms.date: 01/31/2019
apiname:
- _finite
- _finitef
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
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: 1be5aa204a7db3054a49c2e05a8fd77b12ae8a3d
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702749"
---
# <a name="isfinite-finite-finitef"></a>isfinite, _finite, _finitef

Určuje, zda je konečnou hodnotu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

`isfinite` – Makro a `_finite` a `_finitef` funkce vrátí nenulovou hodnotu, pokud *x* je normální nebo subnormal konečná hodnota. Vrátí 0, pokud je argument nekonečno a NaN. Vložené funkce šablony jazyka C++ `isfinite` se chová stejně, ale vrátí **true** nebo **false**.

## <a name="remarks"></a>Poznámky

`isfinite` je makro při kompilaci jako C a vložené funkce šablony při kompilaci jako C++. `_finite` a `_finitef` funkce jsou specifické pro společnost Microsoft. `_finitef` Pouze je funkce dostupná, jenom Pokud sestavili x86, ARM, ARM64 nebo platformy.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h > nebo \<math.h >|\<float.h >, \<math.h >, \<cfloat – >, nebo \<cmath >|
|`isfinite`, `_finitef`|\<math.h>|\<Math.h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isinf –](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
