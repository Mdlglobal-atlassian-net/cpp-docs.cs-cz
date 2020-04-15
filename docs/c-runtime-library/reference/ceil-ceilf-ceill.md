---
title: ceil, ceilf, ceill
ms.date: 4/2/2020
api_name:
- ceilf
- ceil
- ceill
- _o_ceil
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ceil
- ceilf
- ceill
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
ms.openlocfilehash: 7567e5758e405235bca13bbae8a18c2d42ccbd3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333562"
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill

Vypočítá strop hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Hodnota s plovoucí desetinnou táceckou.

## <a name="return-value"></a>Návratová hodnota

Funkce **ceil** vrátí hodnotu s plovoucí desetinnou hodnotou, která představuje nejmenší celé číslo, které je větší nebo rovno *x*. Neexistuje žádná chyba vrátit.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|Žádná|**_DOMAIN**|

**ceil** má implementaci, která používá streaming SIMD extensions 2 (SSE2). Informace a omezení týkající se použití implementace SSE2 naleznete [v tématu _set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že C++ umožňuje přetížení, můžete volat přetížení **ceil,** které trvat **float** nebo **dlouhé** **dvojité** typy. V programu C **ceil** vždy bere a vrací **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ceil**, **ceilf**, **ceill**|\<math.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [podlahu](floor-floorf-floorl.md).

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
