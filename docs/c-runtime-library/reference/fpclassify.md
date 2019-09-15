---
title: fpclassify
ms.date: 04/05/2018
api_name:
- fpclassify
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
api_type:
- HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: e9b5aa1f7dc20cc920a51c2c36371eb907469875
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957065"
---
# <a name="fpclassify"></a>fpclassify

Vrátí klasifikaci argumentu s plovoucí desetinnou čárkou.

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
Hodnota s plovoucí desetinnou čárkou, která má být testována.

## <a name="return-value"></a>Návratová hodnota

**fpclassify –** vrací celočíselnou hodnotu, která označuje třídu s plovoucí desetinnou čárkou argumentu *x*. Tato tabulka zobrazuje možné hodnoty vrácené funkcí **fpclassify –** , které jsou definovány \<v Math. h >.

|Value|Popis|
|-----------|-----------------|
|**FP_NAN**|Tiché, signalizace nebo neurčitý NaN|
|**FP_INFINITE**|Kladné nebo záporné nekonečno|
|**FP_NORMAL**|Kladná nebo záporná normalizovaná nenulová hodnota|
|**FP_SUBNORMAL**|Kladná nebo záporná Denormalizovaná hodnota|
|**FP_ZERO**|Kladná nebo záporná nulová hodnota|

## <a name="remarks"></a>Poznámky

V jazyce C je **fpclassify –** makro; v C++systému je **fpclassify –** funkce přetížená pomocí typů argumentů typu **float**, **Double**nebo **Long** **Double**. V obou případech je vrácená hodnota záviset na skutečném typu výrazu argumentu, a ne u žádné mezilehlé reprezentace. Například hodnota normální **dvojité** nebo dlouhodobé hodnoty **Double** může při převodu na typ **float**způsobit nekonečno, denormální nebo nulovou hodnotu.

## <a name="requirements"></a>Požadavky

|Funkce nebo makro|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<Math. h >|\<Math. h > nebo \<cmath >|

**Fpclassify –** makro a funkce **fpclassify –** odpovídají specifikacím ISO C99 a c++ 11. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
