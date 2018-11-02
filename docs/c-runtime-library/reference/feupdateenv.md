---
title: feupdateenv
ms.date: 04/05/2018
apiname:
- feupdateenv
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
- feupdateenv
- fenv/feupdateenv
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 6d553d6899f55f5bdfb3ff313e88abfcb56ab4ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605104"
---
# <a name="feupdateenv"></a>feupdateenv

Uloží aktuálně vyvolanou výjimky s plovoucí desetinnou čárkou, obnoví stav zadané prostředí s plovoucí desetinnou čárkou a poté vyvolá uložené výjimky s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel **fenv_t** objekt, který obsahuje prostředí s plovoucí desetinnou čárkou jako sada voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Pomocí makra FE_DFL_ENV můžete zadat také výchozí spouštěcí prostředí s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud všechny akce úspěšně dokončila. V opačném případě vrací nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Feupdateenv** funkce provádí různé akce. Nejprve uloží aktuální stav příznaky vyvolanou výjimku plovoucí desetinné čárky v automatického úložiště. Potom nastaví aktuální prostředí s plovoucí desetinnou čárkou z hodnoty uložené v **fenv_t** objekt, který odkazuje *penv*. Pokud *penv* není **FE_DFL_ENV** nebo neodkazuje na platnou **fenv_t** objektu, následné chování není definováno. Nakonec **feupdateenv** vyvolá místně uložené výjimky s plovoucí desetinnou čárkou.

Pokud chcete používat tuto funkci, musíte vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
