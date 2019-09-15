---
title: _get_fmode
ms.date: 11/04/2016
api_name:
- _get_fmode
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
ms.openlocfilehash: 03e07ea44aadec7c15352bb63fd25aa777ee9bfb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955886"
---
# <a name="_get_fmode"></a>_get_fmode

Získá výchozí režim překladu souborů pro vstupně-výstupní operace se soubory.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_fmode(
   int * pmode
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Ukazatel na celé číslo, který má být vyplněn aktuálním výchozím režimem: **_O_TEXT** nebo **_O_BINARY**.

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu v případě úspěchu; chybový kód při selhání. Pokud má Pmode **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce získá hodnotu globální proměnné [_fmode](../../c-runtime-library/fmode.md) . Tato proměnná Určuje výchozí režim překladu souborů pro vstupně-výstupní operace v/v souboru datového proudu, například **_open**, **_pipe**, **fopen**a [freopen](freopen-wfreopen.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_set_fmode](set-fmode.md).

## <a name="see-also"></a>Viz také:

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[I/O soubor textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
