---
title: log1p – log1pf –, log1pl2
ms.date: 04/05/2018
apiname:
- log1p
- log1pf
- log1pl
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
ms.openlocfilehash: 2ac864d7e28823c95b0202c0a8f2454d03c64aff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285983"
---
# <a name="log1p-log1pf-log1pl"></a>log1p – log1pf –, log1pl

Vypočítá přirozený logaritmus 1 a zadané hodnoty.

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

*x*<br/>
Argument s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí fyzická (základní -*e*) z protokolu (*x* + 1).

V opačném případě může vracet instanci jednoho z následujících hodnot:

|Vstup|Výsledek|Výjimka SEH|errno|
|-----------|------------|-------------------|-----------|
|+ inf|+ inf|||
|Denormals|Stejné jako vstup|PODTEČENÍ||
|±0|Stejné jako vstup|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|NaN|NEPLATNÝ|EDOM|
|-inf|NaN|NEPLATNÝ|EDOM|
|±SNaN|Stejné jako vstup|NEPLATNÝ||
|±QNaN nekonečno|Stejné jako vstup|||

**Errno** hodnota nastavená na ERANGE Pokud *x* = -1. **Errno** nastavena na hodnotu **EDOM** Pokud *x* < -1.

## <a name="remarks"></a>Poznámky

**Log1p –** funkce mohou mít přesnější, než pomocí `log(x + 1)` při *x* blíží 0.

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **log1p –** , která používají a vrací **float** a **dlouhé** **double** typy. V programu jazyka C **log1p –** vždy převezme a vrátí **double**.

Pokud *x* přirozené číslo, je tato funkce vrací logaritmus faktoriál (*x* – 1).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**log1p**, **log1pf**, **log1pl**|\<math.h>|\<cmath>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
