---
title: srand – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7972ddfe6ae9c1d591bdbd4cc5e208d78e826037
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107523"
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
