---
title: fesetenv
ms.date: 04/05/2018
apiname:
- fesetenv
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 8c91bfbb89df964fed0a632d5fb5ebac47ebe948
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436145"
---
# <a name="fesetenv"></a>fesetenv

Nastaví aktuální prostředí s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel **fenv_t** objekt, který obsahuje prostředí s plovoucí desetinnou čárkou jako sada voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Můžete také zadat výchozí spouštěcí prostředí s plovoucí desetinnou čárkou pomocí **FE_DFL_ENV** – makro.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud prostředí byl úspěšně nastaven. V opačném případě vrací nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Fesetenv** funkce nastaví aktuální prostředí s plovoucí desetinnou čárkou z hodnoty uložené v **fenv_t** objekt, který odkazuje *penv*. Plovoucí bodu prostředí je sada příznaky stavu a ovládací prvek režimy, které ovlivňují výpočtů s plovoucí desetinnou čárkou. To zahrnuje režimu zaokrouhlování a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud *penv* není **FE_DFL_ENV** nebo neodkazuje na platnou **fenv_t** objektu, následné chování není definováno.

Voláním této funkce nastaví výjimku příznaky stavu, které jsou v *penv* objektu, ale nevyvolá těchto výjimek.

Pokud chcete používat tuto funkci, musíte vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
