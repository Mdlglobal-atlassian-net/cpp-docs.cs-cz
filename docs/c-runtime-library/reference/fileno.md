---
title: _fileno
ms.date: 11/04/2016
apiname:
- _fileno
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
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: 682ab4b01a663bd9a6314138aa692b1c05b7437a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646603"
---
# <a name="fileno"></a>_fileno

Získá popisovač souboru přidruženého datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel **souboru** struktury.

## <a name="return-value"></a>Návratová hodnota

**_fileno** vrátí popisovač souboru. Není vrácena žádná chyba. Výsledek není definován, pokud *stream* neurčuje otevřený soubor. Pokud je datový proud **NULL**, **_fileno** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce vrátí hodnotu -1 a nastaví **errno** k **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Pokud **stdout** nebo **stderr** není spojen s výstupní datový proud (například v aplikaci Windows bez okna konzoly), je popisovač souboru vrátil -2. V předchozích verzích byla popisovač souboru, vrátí -1. Tato změna umožňuje aplikace dokázaly rozlišit k tomuto stavu z chyby.

## <a name="remarks"></a>Poznámky

**_Fileno** rutina vrátí popisovač souboru, který je aktuálně přiřazen k *stream*. Tato rutina se implementuje jako funkce i makra. Informace o výběru některé implementace naleznete v tématu [výběru mezi funkcemi a makry](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
