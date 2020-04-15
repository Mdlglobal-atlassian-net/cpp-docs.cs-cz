---
title: _get_fmode
ms.date: 4/2/2020
api_name:
- _get_fmode
- _o__get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: fbaa30d0842400037f37508df94726f3e7fd7090
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345159"
---
# <a name="_get_fmode"></a>_get_fmode

Získá výchozí režim překladu souborů pro operace vstupně-va souboru.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Ukazatel na celé číslo, které má být vyplněno aktuálním výchozím režimem: **_O_TEXT** nebo **_O_BINARY**.

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu, pokud je úspěšná; kód chyby při selhání. Pokud *pmode* je **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce získá hodnotu globální proměnné [_fmode.](../../c-runtime-library/fmode.md) Tato proměnná určuje výchozí režim překladu souborů pro operace vstupně-out a videa datového proudu, jako jsou **_open**, **_pipe**, **fopen**a [freopen](freopen-wfreopen.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad v [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Viz také

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[Vstupně-to-v. soubor u textu a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
