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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 21bba72b204f975b806e43cdc6d36d8efa173b9b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911432"
---
# <a name="log1p-log1pf-log1pl"></a>log1p –, log1pf –, log1pl

Vypočítá přirozený logaritmus hodnoty 1 a zadanou hodnotu.

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

*znak*<br/>
Argument s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Je-li to úspěšné, vrátí přirozený (základní-*e*) protokol (*x* + 1).

V opačném případě může vracet jednu z následujících hodnot:

|Vstup|Výsledek|Výjimka SEH|errno|
|-----------|------------|-------------------|-----------|
|+ INF|+ INF|||
|Denormalizované|Stejné jako vstup|PODTEČENÍ||
|± 0|Stejné jako vstup|||
|-1|– INF|DIVBYZERO|ERANGE|
|<-1|pak|NENÍ|EDOM|
|– INF|pak|NENÍ|EDOM|
|± SNaN|Stejné jako vstup|NENÍ||
|QNaN, neomezeno|Stejné jako vstup|||

Hodnota **errno** je nastavená na ERANGE, pokud *x* =-1. Hodnota **errno** je nastavená na **EDOM** , pokud *x* <-1.

## <a name="remarks"></a>Poznámky

Funkce **log1p –** můžou být přesnější než při použití `log(x + 1)` , když je *x* blízko 0.

Vzhledem k tomu, že jazyk C++ umožňuje přetížení, můžete volat přetížení **log1p –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **log1p –** vždycky přebírá a vrací **Double**.

Pokud je *x* přirozené číslo, vrátí tato funkce logaritmus faktoriál (*x* -1).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|Hlavička C++|
|--------------|--------------|------------------|
|**log1p –**, **log1pf –**, **log1pl**|\<Math. h>|\<cmath>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
