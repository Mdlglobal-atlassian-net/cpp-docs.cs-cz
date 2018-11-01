---
title: fegetenv
ms.date: 04/05/2018
apiname:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: d3985e4dd2b3944bcdddb79605887def7ba15473
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668088"
---
# <a name="fegetenv"></a>fegetenv

Uloží aktuální prostředí s plovoucí desetinnou čárkou zadaného objektu.

## <a name="syntax"></a>Syntaxe

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel **fenv_t** objekt obsahovat aktuální hodnoty s plovoucí desetinnou čárkou prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud prostředí s plovoucí desetinnou čárkou byl úspěšně uložen v *penv*. V opačném případě vrací nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Fegetenv** funkce ukládá aktuální prostředí s plovoucí desetinnou čárkou v objektu, na které odkazuje *penv*. Plovoucí bodu prostředí je sada příznaky stavu a ovládací prvek režimy, které ovlivňují výpočtů s plovoucí desetinnou čárkou. To zahrnuje režimu zaokrouhlení směrem a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud *penv* neodkazuje na platnou **fenv_t** objektu, následné chování není definováno.

Pokud chcete používat tuto funkci, musíte vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
