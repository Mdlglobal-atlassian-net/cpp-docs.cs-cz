---
title: fpclassify –
ms.date: 04/05/2018
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: a25897a110d96923a45695d61f923dc7818c7e3a
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518357"
---
# <a name="fpclassify"></a>fpclassify –

Vrátí hodnotu s plovoucí desetinnou čárkou klasifikace argumentu.

## <a name="syntax"></a>Syntaxe

```C
int fpclassify(
   /* floating-point */ x
);

int fpclassify(
   float x
); // C++ only

int fpclassify(
   double x
); // C++ only

int fpclassify(
   long double x
); // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

**fpclassify –** vrací celočíselnou hodnotu, která určuje třídu s plovoucí desetinnou čárkou argumentu *x*. Tato tabulka uvádí možné hodnoty vrácené **fpclassify –** definované v \<math.h >.

|Hodnota|Popis|
|-----------|-----------------|
|**FP_NAN**|Tichý, signalizace nebo neurčitý NaN|
|**FP_INFINITE**|Kladné nebo záporné nekonečno|
|**FP_NORMAL**|Kladná nebo záporná normalizované nenulová hodnota|
|**FP_SUBNORMAL**|Kladná nebo záporná hodnota Nenormalizovaná|
|**FP_ZERO**|Pozitivní nebo negativní nulovou hodnotu|

## <a name="remarks"></a>Poznámky

V jazyce C **fpclassify –** je makro; v jazyce C++, **fpclassify –** je funkce přetížena, pomocí argumentu typu **float**, **double**, nebo **dlouhé** **double**. V obou případech se vrácená hodnota závisí na platné typu výraz argumentu a nikoli na všechny zprostředkující reprezentace. Například normální **double** nebo **dlouhé** **double** hodnota stane nekonečno, denormal nebo při převodu na hodnotu nula **float**.

## <a name="requirements"></a>Požadavky

|Funkce nebo makra|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<Math.h >|\<Math.h > nebo \<cmath >|

**Fpclassify –** – makro a **fpclassify –** funkce v souladu s normou ISO C99 a C ++ 11 specifikace. Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
