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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a12c0c93ae15350a4b91a8aa905acb941f8b6a10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345034"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

Načte popisovač souboru operačního systému, který je přidružen k zadanému popisovači souboru.

## <a name="syntax"></a>Syntaxe

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Existující popisovač souboru.

## <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru operačního systému, pokud je *fd* platný. V opačném případě je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, vrátí **INVALID_HANDLE_VALUE** (-1). Také nastaví **errno** na **EBADF**, označující neplatný popisovač souboru. Chcete-li se vyhnout upozornění při použití výsledku jako popisovač souboru Win32, přetypujte jej na typ **HANDLE.**

> [!NOTE]
> Když **stdin**, **stdout**a **stderr** nejsou přidruženy k datovému proudu (například v aplikaci systému Windows bez okna konzoly), hodnoty popisovače souborů pro tyto datové proudy jsou vráceny z [_fileno](fileno.md) jako speciální hodnota -2. Podobně pokud použijete parametr 0, 1 nebo 2 jako parametr popisovače souboru namísto výsledku volání **_fileno**, **vrátí _get_osfhandle** také speciální hodnotu -2, pokud popisovač souboru není přidružen k datovému proudu a nenastaví **chybné číslo**. To však není platná hodnota popisovače souboru a následná volání, která se pokoušejí použít, se pravděpodobně nezdaří.

Další informace o **EBADF** a dalších kódech chyb naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Chcete-li zavřít soubor, jehož popisovač souboru operačního systému (OS) získá **_get_osfhandle**, volání [_close](close.md) na popisovač souboru *fd*. Nikdy volat **CloseHandle** na vrácenou hodnotu této funkce. Základní popisovač souboru operačního systému je vlastněn popisovačem souboru *fd* a je uzavřen, když [je _close](close.md) volána na *fd*. Pokud je popisovač souboru `FILE *` vlastněn datovým proudem, pak volání [fclose](fclose-fcloseall.md) na tomto `FILE *` datovém proudu zavře popisovač souboru i základní popisovač souboru operačního systému. V takovém případě nevolejte [_close](close.md) popisovače souboru.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
