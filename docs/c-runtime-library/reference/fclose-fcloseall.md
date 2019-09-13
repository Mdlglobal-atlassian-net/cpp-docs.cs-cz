---
title: fclose, _fcloseall
ms.date: 11/04/2016
api_name:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 215925fb16f5d51e481ae92cbb45b0270bd5ebd4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941507"
---
# <a name="fclose-_fcloseall"></a>fclose, _fcloseall

Zavře datový proud (**fclose**) nebo zavře všechny otevřené streamy ( **_fcloseall**).

## <a name="syntax"></a>Syntaxe

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

**fclose** vrátí hodnotu 0, pokud byl datový proud úspěšně zavřen. **_fcloseall** vrátí celkový počet uzavřených datových proudů. Obě funkce vrací **EOF** pro indikaci chyby.

## <a name="remarks"></a>Poznámky

Funkce **fclose** ukončí *datový proud*. Pokud má *datový proud* **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **fclose** nastaví **errno** na **EINVAL** a vrátí **EOF**. Doporučuje se před voláním této funkce vždy zkontrolovat ukazatel na *datový proud* .

Další informace o těchto a dalších chybových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

Funkce **_fcloseall** zavře všechny otevřené streamy kromě **stdin**, **stdout**, **stderr** (a v systémech MS-DOS, **_stdaux** a **_stdprn**). Také se zavře a odstraní všechny dočasné soubory vytvořené nástrojem **tmpfile**. V obou funkcích jsou před zavřením vyprázdněny všechny vyrovnávací paměti spojené s datovým proudem. Po zavření datového proudu jsou uvolněny vyrovnávací paměti přidělené systémem. Vyrovnávací paměti přiřazené uživatelem s **setbuf** a **setvbuf –** nejsou automaticky uvolněny.

**Poznámka:** Pokud jsou tyto funkce použity k zavření datového proudu, jsou zavřeny podkladové popisovače souborů a popisovač souboru operačního systému (nebo soket) a také datový proud. Proto pokud byl soubor původně otevřen jako popisovač souboru nebo popisovač souboru a je uzavřený pomocí **fclose**, Nevolejte také **_close** pro zavření popisovače souboru; Nevolejte **CloseHandle** funkce Win32 pro zavření popisovače souboru.

**fclose** a **_fcloseall** obsahují kód pro ochranu proti rušení z jiných vláken. Neuzamykání verze **fclose**naleznete v tématu **_fclose_nolock**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
