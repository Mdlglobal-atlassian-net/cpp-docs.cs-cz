---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 04/05/2018
apiname:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: 01680a62e654112475a55bd8eac0cc14d254e2a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285769"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Zadaná hodnota s plovoucí desetinnou čárkou na nejbližší celočíselnou hodnotu, zaokrouhlí na základě aktuální režim zaokrouhlování a směr.

## <a name="syntax"></a>Syntaxe

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota má být zaokrouhleno.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí zaoblenými hodnota integrálního *x*.

|Problém|Vrátí|
|-----------|------------|
|*x* je mimo rozsah návratový typ<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|Vyvolá **FE_INVALID** a vrací nulu (0).|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **lrint** a **llrint** trvají **float** a **dlouhé**  **dvojité** typy. V programu jazyka C **lrint** a **llrint** vždy směrují **double**.

Pokud *x* nepředstavuje s plovoucí desetinnou čárkou ekvivalent celočíselnou hodnotu, tato funkce vyvolá **FE_INEXACT**.

**Specifické pro Microsoft**: Pokud výsledek je mimo rozsah návratového typu nebo pokud je parametr nekonečno a NaN, vrácená hodnota je definován implementací. Kompilátor společnosti Microsoft vrátí nulové hodnoty (0).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
