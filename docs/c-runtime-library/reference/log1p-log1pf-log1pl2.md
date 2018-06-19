---
title: log1p – log1pf –, log1pl2 | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 650fb8f7567b4f2f3b0b9032397c2b54a99013dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402745"
---
# <a name="log1p-log1pf-log1pl"></a>log1p – log1pf –, log1pl

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

*x*<br/>
Argumentem s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí přirozený (základní -*e*) protokolu systému (*x* + 1).

Jinak může vrátit jednu z následujících hodnot:

|Vstup|Výsledek|Výjimka SEH|Kód chyby|
|-----------|------------|-------------------|-----------|
|+ inf|+ inf|||
|Denormals|Stejné jako vstup|PODTEČENÍ||
|±0|Stejné jako vstup|||
|-1|-inf|DIVBYZERO|ERANGE –|
|< -1|NaN.|NEPLATNÝ|EDOM –|
|-inf|NaN.|NEPLATNÝ|EDOM –|
|±SNaN|Stejné jako vstup|NEPLATNÝ||
|±QNaN neomezené|Stejné jako vstup|||

**Errno** hodnota nastavena na erange – Pokud *x* = -1. **Errno** nastavena na hodnotu **edom –** Pokud *x* < -1.

## <a name="remarks"></a>Poznámky

**Log1p –** funkce může být přesnější, než pomocí `log(x + 1)` při *x* blíží 0.

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **log1p –** , přijmout a vrátit **float** a **dlouho** **dvojité** typy. V programu C **log1p –** vždy provede a vrátí **dvojité**.

Pokud *x* přirozený číslo, vrátí tato funkce logaritmus faktoriál (*x* - 1).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**log1p –**, **log1pf –**, **log1pl**|\<Math.h >|\<cmath – >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
