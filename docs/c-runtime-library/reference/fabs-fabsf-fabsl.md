---
title: fabs, fabsf, fabsl
ms.date: 04/05/2018
api_name:
- fabsf
- fabs
- fabsl
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
ms.openlocfilehash: 155b0e4ced7eb4ea0ade5445a62fc385f0c157e9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941484"
---
# <a name="fabs-fabsf-fabsl"></a>fabs, fabsf, fabsl

Vypočítá absolutní hodnotu argumentu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Funkce **fabs –** vrací absolutní hodnotu argumentu *x*. Nevrátila se žádná chybová zpráva.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|QNAN, ZASÁHNOUT|žádná|_DOMAIN|

## <a name="remarks"></a>Poznámky

C++umožňuje přetížení, takže můžete volat přetížení **fabs –** , pokud zahrnete \<hlavičku cmath >. V programu v jazyce C **fabs –** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Povinné záhlaví jazyka C|Požadovaná C++ hlavička|
|--------------|-----------------------|---------------------------|
|**fabs –** , **fabsf –** , **fabsl**|\<Math. h >|\<cmath > nebo \<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [ABS](abs-labs-llabs-abs64.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
