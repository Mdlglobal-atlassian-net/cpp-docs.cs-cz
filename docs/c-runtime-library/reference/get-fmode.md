---
title: _get_fmode
ms.date: 11/04/2016
apiname:
- _get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_fmode
- _get_fmode
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
ms.openlocfilehash: dc4740b20ab7283dd8b9f73f458eaba34e582832
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328042"
---
# <a name="getfmode"></a>_get_fmode

Získá výchozí režim překladu souboru pro soubor vstupně-výstupních operací.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Ukazatel na celé číslo tankujeme aktuální výchozí režim: **_O_TEXT** nebo **_O_BINARY**.

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu v případě úspěchu; Kód chyby při selhání. Pokud *pmode* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Získá hodnotu funkce [_fmode](../../c-runtime-library/fmode.md) globální proměnné. Tato proměnná Určuje výchozí režim překladu souboru pro obě nízké úrovně a streamování vstupně-výstupní operace, jako například **_Otevřít**, **_pipe –**, **fopen**, a [ freopen](freopen-wfreopen.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_set_fmode –](set-fmode.md).

## <a name="see-also"></a>Viz také:

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[I/O soubor textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
