---
title: _get_osfhandle
ms.date: 4/2/2020
api_name:
- _get_osfhandle
- _o__get_osfhandle
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: 085bf20a12d9b77be0977521bde2ab75d9b2636a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918287"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

Načte popisovač souborů operačního systému, který je přidružený k zadanému popisovači souboru.

## <a name="syntax"></a>Syntaxe

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Existující popisovač souboru.

## <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru operačního systému, pokud je *FD* platný. V opačném případě je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí **INVALID_HANDLE_VALUE** (-1). Nastaví také **errno** na **EBADF**, což značí neplatný popisovač souboru. Chcete-li se vyhnout upozornění, když je výsledek použit jako popisovač souboru Win32, přetypujte jej na typ **popisovače** .

> [!NOTE]
> Když se **stdin**, **stdout**a **stderr** nevztahují ke streamu (například v aplikaci Windows bez okna konzoly), hodnoty popisovačů souborů pro tyto datové proudy se vrátí z [_fileno](fileno.md) jako speciální hodnota – 2. Podobně pokud použijete 0, 1 nebo 2 jako parametr popisovače souboru namísto volání metody **_fileno**, **_get_osfhandle** také vrátí speciální hodnotu-2, pokud popisovač souboru není přidružen ke streamu a nenastaví **errno**. Nejedná se však o platnou hodnotu popisovače souboru a následné volání, která se pokoušejí použít, budou pravděpodobně neúspěšná.

Další informace o **EBADF** a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Chcete-li zavřít soubor, jehož popisovač souboru operačního systému (OS) je získán nástrojem **_get_osfhandle**, zavolejte [_close](close.md) v popisovači souboru *FD*. Pro návratovou hodnotu této funkce nikdy Nevolejte **CloseHandle** . Popisovač souboru podkladového operačního systému je vlastněn popisovačem souboru *FD* a je uzavřen, když je [_close](close.md) volána v *FD*. Pokud popisovač souboru vlastní `FILE *` datový proud, pak voláním [fclose](fclose-fcloseall.md) v tomto `FILE *` datovém proudu se zavře popisovač souboru i podkladový popisovač souboru operačního systému. V takovém případě Nevolejte [_close](close.md) v popisovači souboru.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_osfhandle**|\<IO. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
