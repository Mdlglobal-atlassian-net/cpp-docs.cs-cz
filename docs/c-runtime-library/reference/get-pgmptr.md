---
title: _get_pgmptr
ms.date: 4/2/2020
api_name:
- _get_pgmptr
- _o__get_pgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: efcac6a64c01bee38a3753bdec378dae625db35e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345021"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

Získá aktuální hodnotu **_pgmptr** globální proměnné.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>Parametry

*pHodnota*<br/>
Ukazatel na řetězec, který má být vyplněn aktuální hodnotou **proměnné _pgmptr.**

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu, pokud je úspěšná; kód chyby při selhání. Pokud je *hodnota pValue* **null**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

## <a name="remarks"></a>Poznámky

Volání **_get_pgmptr** pouze v případě, že váš program má úzký vstupní bod, například **main()** nebo **WinMain()**. Globální proměnná **_pgmptr** obsahuje úplnou cestu ke spustitelnému souboru přidruženému k procesu. Další informace naleznete [v tématu _pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_get_wpgmptr](get-wpgmptr.md)<br/>
