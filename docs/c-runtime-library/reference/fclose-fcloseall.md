---
title: fclose, _fcloseall
ms.date: 11/04/2016
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 4713ffb7ecdf8da73e5f949bbef7be124dfaf28a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334876"
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall

Zavře datový proud (**fclose –**) nebo zavře všechny otevřené datové proudy (**_fcloseall**).

## <a name="syntax"></a>Syntaxe

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**fclose –** vrátí hodnotu 0, pokud datový proud je uzavřen úspěšně. **_fcloseall** vrátí celkový počet datových proudů uzavřen. Obě funkce vrátí **EOF** udávající chybu.

## <a name="remarks"></a>Poznámky

**Fclose –** funkce zavře *stream*. Pokud *stream* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **fclose –** nastaví **errno** k **EINVAL** a vrátí **EOF**. Dále je doporučeno *stream* ukazatel vždy kontrolovány před voláním této funkce.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

**_Fcloseall** funkce zavře všechny otevřené datových proudů s výjimkou **stdin**, **stdout**, **stderr** (a v operačním systému MS-DOS, **_stdaux**  a **_stdprn**). Také se zavře a odstraní všechny dočasných souborů vytvořených databázovým **tmpfile –**. V obou funkcí, před uzavírací vyprázdní všechny vyrovnávací paměti přidružený datový proud. System – přidělené vyrovnávací paměti se vydávají při datový proud je uzavřen. Vyrovnávací paměti přiřazené uživatelem s **setbuf –** a **setvbuf –** nedojde k uvolnění automaticky.

**Poznámka:** V případě tyto funkce používají zavřete datový proud, podkladového popisovače souborů a operačním systémem popisovač souboru (nebo soketu) jsou uzavřeny, a také datového proudu. Proto pokud soubor byl původně otevřen jako soubor zpracování nebo popisovač souboru a je uzavřen **fclose –**, proveďte volání není také **_Zavřít** na zavřít popisovač souboru; nelze volat funkci Win32  **CloseHandle** zavřít popisovač souboru.

**fclose –** a **_fcloseall** přidat kód pro ochranu před rušením z jiných vláken. Nezamykací verze nástroje **fclose –**, naleznete v tématu **_fclose_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fclose –**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fopen](fopen-wfopen.md).

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
