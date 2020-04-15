---
title: _get_wpgmptr
ms.date: 4/2/2020
api_name:
- _get_wpgmptr
- _o__get_wpgmptr
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
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 1e54d3dbdc837c491f5b39d33a9b8197094ac60b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344869"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

Získá aktuální hodnotu globální proměnné **_wpgmptr.**

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Parametry

*pHodnota*<br/>
Ukazatel na řetězec, který má být vyplněn aktuální hodnotou **proměnné _wpgmptr.**

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu, pokud je úspěšná; kód chyby při selhání. Pokud je *hodnota pValue* **null**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **Funkce EINVAL**.

## <a name="remarks"></a>Poznámky

Volání **_get_wpgmptr** pouze v případě, že program má široký vstupní bod, jako **je wmain()** nebo **wWinMain()**. Globální proměnná **_wpgmptr** obsahuje úplnou cestu ke spustitelnému souboru přidruženému k procesu jako řetězec s širokým znakem. Další informace naleznete [v tématu _pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_get_pgmptr](get-pgmptr.md)<br/>
