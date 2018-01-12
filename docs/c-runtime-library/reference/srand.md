---
title: "srand – | Microsoft Docs"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: srand
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
f1_keywords: srand
dev_langs: C++
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
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 205dcb2ba7d61dff1286fd926e3f10cf2a162e9a
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="srand"></a>srand

Nastaví počáteční počáteční hodnoty pro generátor pseudonáhodných čísel používané `rand` funkce.

## <a name="syntax"></a>Syntaxe

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*počáteční hodnoty*  
Počáteční hodnota pro generování pseudonáhodných čísel

## <a name="remarks"></a>Poznámky

Funkce `srand` nastaví počáteční bod pro generování posloupnosti pseudonáhodných celých čísel v aktuálním vlákně. Chcete-li znovu inicializovat generátoru pro vytvoření stejné pořadí výsledků, volejte `srand` funkce a používat stejné *počáteční hodnoty* argument znovu. Žádné jiné hodnoty pro *počáteční hodnoty* nastaví generátor pro různé výchozí bod v pseudonáhodných pořadí. Funkce `rand` načte pseudonáhodná čísla, která jsou generována. Volání metody `rand` před voláním jakékoli `srand` generuje stejném pořadí jako volání `srand` s *počáteční hodnoty* předány jako 1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`srand`|\<stdlib.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [rand –](../../c-runtime-library/reference/rand.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)  
[rand](../../c-runtime-library/reference/rand.md)  
