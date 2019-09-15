---
title: isfinite, _finite, _finitef
ms.date: 01/31/2019
api_name:
- _finite
- _finitef
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a2cde4d3a57884413f0c48aa299b171334c5f988
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957185"
---
# <a name="isfinite-_finite-_finitef"></a>isfinite, _finite, _finitef

Určuje, zda je hodnota s plovoucí desetinnou čárkou konečná.

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
Hodnota s plovoucí desetinnou čárkou, která má být testována.

## <a name="return-value"></a>Návratová hodnota

Makro a funkce`_finitef` a vrátí nenulovou hodnotu, pokud x je buď normální, nebo normální konečná hodnota. `isfinite` `_finite` Vrátí 0, pokud je argument nekonečný nebo NaN. C++ Vložená funkce `isfinite` šablony se chová stejným způsobem, ale vrátí **hodnotu true** nebo **false**.

## <a name="remarks"></a>Poznámky

`isfinite`je makro při kompilaci jako C a vložená funkce šablony, která je kompilována C++jako. Funkce `_finite` a`_finitef` jsou specifické pro společnost Microsoft. `_finitef` Funkce je k dispozici pouze při kompilování pro platformy x86, ARM nebo ARM64.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float. h > nebo \<Math. h >|\<float. h >, \<Math. h >, \<cfloat > nebo \<cmath >|
|`isfinite`, `_finitef`|\<Math. h >|\<Math. h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
