---
title: fegetenv | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc8b5d189838c2788bc6200f9072c9511e61d42f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fegetenv"></a>fegetenv

Uloží aktuální prostředí s plovoucí desetinnou čárkou v zadaný objekt.

## <a name="syntax"></a>Syntaxe

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel na **fenv_t** objekt, který chcete obsahují aktuální hodnoty s plovoucí desetinnou čárkou prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je s plovoucí desetinnou čárkou prostředí byl úspěšně uložen v *penv*. Jinak vrátí hodnotu nula.

## <a name="remarks"></a>Poznámky

**Fegetenv** funkce uloží aktuální prostředí s plovoucí desetinnou čárkou v objektu, na kterou odkazuje *penv*. Procedura bodu prostředí je sada příznaky stavu a řízení režimy, které ovlivňují výpočty s plovoucí desetinnou čárkou. To zahrnuje režim směr zaokrouhlení a příznaky stavu pro výjimky s plovoucí desetinnou čárkou.  Pokud *penv* neodkazuje na platný **fenv_t** objektu následné chování není definován.

Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
