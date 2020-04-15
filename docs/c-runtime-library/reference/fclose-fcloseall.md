---
title: fclose, _fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: b2ee14c5fc8bb47cc2652443c0263bd14147c90d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347495"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Zavře datový proud (**fclose**) nebo zavře všechny otevřené datové proudy (**_fcloseall**).

## <a name="syntax"></a>Syntaxe

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

**fclose** vrátí 0, pokud je datový proud úspěšně uzavřen. **_fcloseall** vrátí celkový počet uzavřených datových proudů. Obě funkce vrátí **EOF** označující chybu.

## <a name="remarks"></a>Poznámky

Funkce **fclose** zavře *datový proud*. Pokud je *datový proud* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **fclose** sady **errno** na **EINVAL** a vrátí **EOF**. Doporučuje se, aby ukazatel *datového proudu* vždy zkontrolovat před voláním této funkce.

Další informace o těchto a dalších kódech chyb naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

Funkce **_fcloseall** zavře všechny otevřené proudy kromě **stdin**, **stdout**, **stderr** (a v Systému MS-DOS **_stdaux** a **_stdprn**). Také zavře a odstraní všechny dočasné soubory vytvořené **tmpfile**. V obou funkcích jsou všechny vyrovnávací paměti přidružené k datovému proudu vyprázdněny před zavřením. Systémové rezervy jsou uvolněny při zavření datového proudu. Vyrovnávací paměti přiřazené uživatelem s **setbuf** a **setvbuf** nejsou automaticky uvolněny.

**Poznámka:** Při použití těchto funkcí k zavření datového proudu, podkladový popisovač souboru a popisovač souboru operačního systému (nebo soket) jsou uzavřeny, stejně jako datový proud. Pokud byl tedy soubor původně otevřen jako popisovač souboru nebo popisovač souboru a je uzavřen **fclose**, nevolejte také **_close** k zavření popisovače souboru; nevolejte win32 funkce **CloseHandle** zavřít popisovač souboru.

**fclose** a **_fcloseall** obsahovat kód pro ochranu proti rušení z jiných vláken. Pokud jde o verzi **fclose**bez uzamčení , viz **_fclose_nolock**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
