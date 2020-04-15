---
title: log1p, log1pf, log1pl2
ms.date: 4/2/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: b4e077f5b806dbe38ed4a4f4e8eef0259170cb7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341812"
---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl

Vypočítá přirozený logaritmus 1 plus zadanou hodnotu.

## <a name="syntax"></a>Syntaxe

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument s plovoucí desetinnou desetinnou a střední.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí přirozený (base-*e*) log (*x* + 1).

V opačném případě může vrátit jednu z následujících hodnot:

|Vstup|Výsledek|Výjimka SEH|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|Denormální jevy|Stejné jako vstup|Podtečení||
|±0|Stejné jako vstup|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1.|Nan|Neplatný|Edom|
|-inf|Nan|Neplatný|Edom|
|±Snan|Stejné jako vstup|Neplatný||
|±QNaN, neurčitý|Stejné jako vstup|||

Hodnota **errno** je nastavena na ERANGE, pokud *x* = -1. Hodnota **errno** je nastavena na **EDOM,** pokud *x* < -1.

## <a name="remarks"></a>Poznámky

Funkce **log1p** mohou být přesnější `log(x + 1)` než *použití,* když x je blízko 0.

Protože C++ umožňuje přetížení, můžete volat přetížení **log1p,** které take a return **float** a **dlouhé** **dvojité** typy. V programu C **log1p** vždy trvá a vrátí **double**.

Pokud *x* je přirozené číslo, vrátí tato funkce logaritmus faktoriálu (*x* - 1).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
