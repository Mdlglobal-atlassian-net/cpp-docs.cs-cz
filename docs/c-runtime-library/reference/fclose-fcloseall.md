---
title: fclose –, _fcloseall – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03e884663c1af1d9c9f31330cda40aa3c7458820
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall

Zavře datového proudu (**fclose –**) nebo, zavře všechny otevřené datové proudy (**_fcloseall –**).

## <a name="syntax"></a>Syntaxe

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

**fclose –** vrátí hodnotu 0, pokud datový proud je uzavřen úspěšně. **_fcloseall –** vrátí celkový počet datových proudů uzavřen. Obě funkce vrátí **EOF** indikující chybu.

## <a name="remarks"></a>Poznámky

**Fclose –** funkce zavře *datového proudu*. Pokud *datového proudu* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **fclose –** nastaví **errno** k **einval –** a vrátí **EOF**. Dále je doporučeno *datového proudu* ukazatel vždy zaškrtnuto před volání této funkce.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.

**_Fcloseall –** funkce zavře všechny otevřené datové proudy s výjimkou **stdin –**, **stdout**, **stderr** (a v MS-DOS, **_stdaux**  a **_stdprn**). Také se zavře a odstraní všechny dočasné soubory vytvořené **tmpfile –**. V obou funkce jsou před uzavírací Vyprázdněné všechny vyrovnávací paměti přidružené datového proudu. Vyrovnávací paměti přidělené systému vydávají při datový proud je uzavřen. Vyrovnávací paměti přiřazené uživatelem s **setbuf –** a **setvbuf –** nejsou vydané automaticky.

**Poznámka:** Pokud tyto funkce používají Zavřít datový proud, podkladové popisovače souborů a operačního systému popisovač souboru (nebo soketu) jsou uzavřeny, a také datového proudu. Proto pokud soubor byl původně otevřen jako soubor zpracování nebo soubor popisovače a se zavřel s **fclose –**, ne také provést volání **_close –** k zavřete popisovače souborů; Nevolejte funkce Win32  **Funkce CloseHandle** zavřít popisovač souboru.

**fclose –** a **_fcloseall –** , přidat kód pro ochranu proti rušení jiná vlákna. Bez uzamčení verze nástroje **fclose –**, najdete v části **_fclose_nolock –**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fclose –**|\<stdio.h>|
|**_fcloseall –**|\<stdio.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [fopen –](fopen-wfopen.md).

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
