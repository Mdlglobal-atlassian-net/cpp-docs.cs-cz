---
title: nan, nanf, nanl
ms.date: 4/2/2020
api_name:
- nanf
- nan
- nanl
- _o_nan
- _o_nanf
- _o_nanl
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
- nan
- nanl
- nanf
helpviewer_keywords:
- nan function
- nanf function
- nanl function
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
ms.openlocfilehash: d8f0db5020f274de27f7f1bbf3a76659eae568e4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338646"
---
# <a name="nan-nanf-nanl"></a>nan, nanf, nanl

Vrátí tichou hodnotu NaN.

## <a name="syntax"></a>Syntaxe

```C
double nan( const char* input );
float nanf( const char* input );
long double nanl( const char* input );
```

### <a name="parameters"></a>Parametry

*Vstupní*<br/>
Hodnota řetězce.

## <a name="return-value"></a>Návratová hodnota

**Nan** funkce vrátí tichou hodnotu NaN.

## <a name="remarks"></a>Poznámky

**Nan** funkce vrátí hodnotu s plovoucí desetinnou hodnotou, která odpovídá tiché (nesignalizační) NaN. *Vstupní* hodnota je ignorována. Informace o tom, jak je NaN reprezentovánpro výstup, naleznete [v tématu printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**nan**, **nanf**, **nanl**|\<math.h>|\<cmath> \<nebo math.h>|

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
