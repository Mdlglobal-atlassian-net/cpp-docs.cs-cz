---
title: srand
ms.date: 4/2/2020
api_name:
- srand
- _o_srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: a8d018d429b2a484f88b7c1e0679f1f799983910
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355490"
---
# <a name="srand"></a>srand

Nastaví počáteční hodnotu osiva pro generátor pseudonáhodných čísel používaný funkcí **rand.**

## <a name="syntax"></a>Syntaxe

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*Osiva*<br/>
Počáteční hodnota pro generování pseudonáhodných čísel

## <a name="remarks"></a>Poznámky

Funkce **srand** nastavuje počáteční bod pro generování řady pseudonáhodných celá čísla v aktuálním vlákně. Chcete-li znovu inicializovat generátor a vytvořit stejnou sekvenci výsledků, zavolejte funkci **srand** a znovu použijte stejný argument *počátečního napětí.* Jakákoli jiná hodnota pro *osivo* nastaví generátor na jiný výchozí bod v pseudonáhodné sekvenci. **rand** načte pseudonáhodná čísla, která jsou generována. Volání **rand** před volání **srand** generuje stejnou sekvenci jako volání **srand** s *osivem* předán jako 1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [rand](rand.md).

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[Rand](rand.md)<br/>
