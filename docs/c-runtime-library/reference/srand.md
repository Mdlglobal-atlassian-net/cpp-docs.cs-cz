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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3f6f97ad9a3bd0d7e4e88ad1797d369f012bbe5e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913597"
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

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**srand**|\<Stdlib. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [Rand](rand.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[funkcí](rand.md)<br/>
