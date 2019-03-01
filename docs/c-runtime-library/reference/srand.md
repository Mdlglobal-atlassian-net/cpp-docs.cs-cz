---
title: srand
ms.date: 1/02/2018
apiname:
- srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 6545d4eba6c17fd55bb2b8cf23fb0319d1c96bee
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57209818"
---
# <a name="srand"></a>srand

Nastaví počáteční hodnotu seed pro generátor pseudonáhodných čísel používaný **rand** funkce.

## <a name="syntax"></a>Syntaxe

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*Počáteční hodnota*<br/>
Počáteční hodnota pro generování pseudonáhodných čísel

## <a name="remarks"></a>Poznámky

**Srand –** funkce nastaví výchozí bod pro generování posloupnosti pseudonáhodných celých čísel v aktuálním vlákně. Chcete-li znovu inicializovat generátor vytvořit stejnou sekvenci výsledků, zavolejte **srand –** fungovat a využívat stejné *počáteční hodnoty* argument znovu. Jakákoli jiná hodnota parametru *počáteční hodnoty* nastaví generátor na jiný výchozí bod v pseudonáhodné posloupnosti. **rand** načte pseudonáhodná čísla, která jsou generována. Volání **rand** před voláním **srand –** vygeneruje stejnou posloupnost jako volání funkce **srand –** s *počáteční hodnoty* hodnotou 1 předanou parametru.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [rand](rand.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
