---
title: srand
ms.date: 01/02/2018
api_name:
- srand
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
ms.openlocfilehash: 03e2b87a37d1b520b6e2b32c2f756fea625eb9a2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958001"
---
# <a name="srand"></a>srand

Nastaví počáteční počáteční hodnotu generátoru pseudonáhodných čísel používaného funkcí **Rand** .

## <a name="syntax"></a>Syntaxe

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parametry

*sazení*<br/>
Počáteční hodnota pro generování pseudonáhodných čísel

## <a name="remarks"></a>Poznámky

Funkce **srand** nastaví počáteční bod pro generování řady celých čísel pseudonáhodných v aktuálním vlákně. Chcete-li znovu inicializovat generátor, aby vytvořil stejnou sekvenci výsledků, zavolejte funkci **srand** a použijte stejný argument *počáteční* hodnoty. Jakákoli jiná hodnota pro *počáteční* hodnotu nastaví generátor na jiný výchozí bod v pseudonáhodných sekvenci. **Rand** načítá pseudonáhodných čísla, která jsou generována. Volání **Rand** před jakýmkoli voláním **srand** generuje stejnou sekvenci jako volání **srand** s *osivem* předanou jako 1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [Rand](rand.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
