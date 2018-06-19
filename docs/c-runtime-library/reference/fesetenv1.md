---
title: fesetenv | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd761f505c602aad44c5e00df223d4a6c983e851
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397243"
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
Ukazatel na **fenv_t** objekt, který obsahuje prostředí s plovoucí desetinnou čárkou jako sada voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Můžete také zadat výchozí spouštěcí s plovoucí desetinnou čárkou prostředí pomocí **FE_DFL_ENV** makro.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud prostředí byl úspěšně nastaven. Jinak vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Fesetenv** funkce nastaví z s hodnotou uloženou v aktuálním prostředí s plovoucí desetinnou čárkou **fenv_t** objektu na kterou odkazuje *penv*. Procedura bodu prostředí je sada příznaky stavu a řízení režimy, které ovlivňují výpočty s plovoucí desetinnou čárkou. To zahrnuje zaokrouhlení režimu a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud *penv* není **FE_DFL_ENV** nebo neodkazuje na platný **fenv_t** objektu následné chování není definován.

Volání této funkce nastaví výjimku příznaky stavu, které jsou v *penv* objektu, ale nevyvolá tyto výjimky.

Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
