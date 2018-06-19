---
title: feupdateenv | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d88284717aec7a19c936d7ed8d87da96006d7ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397591"
---
# <a name="feupdateenv"></a>feupdateenv

Uloží aktuálně vyvolané výjimky s plovoucí desetinnou čárkou, obnoví stav zadaného prostředí s plovoucí desetinnou čárkou a poté vyvolá uložené výjimky s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>Parametry

*penv*<br/>
Ukazatel na **fenv_t** objekt, který obsahuje prostředí s plovoucí desetinnou čárkou jako sada voláním [fegetenv](fegetenv1.md) nebo [feholdexcept](feholdexcept2.md). Použití makra FE_DFL_ENV, můžete také zadat výchozí spouštěcí prostředí s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud se všechny akce úspěšně dokončit. Jinak vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

**Feupdateenv** funkce provádí různé akce. Nejprve ukládá aktuální stav příznaky výjimky vyvolané s plovoucí desetinnou čárkou v automatické úložiště. Potom nastaví z s hodnotou uloženou v aktuálním prostředí s plovoucí desetinnou čárkou **fenv_t** objektu na kterou odkazuje *penv*. Pokud *penv* není **FE_DFL_ENV** nebo neodkazuje na platný **fenv_t** objektu následné chování není definován. Nakonec **feupdateenv** vyvolá místně uložené výjimky s plovoucí desetinnou čárkou.

Chcete-li tuto funkci použít, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
