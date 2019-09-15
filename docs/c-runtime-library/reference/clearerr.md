---
title: clearerr
ms.date: 11/04/2016
api_name:
- clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 9fd2f7e7dfcf272e806a887b356418b7555913f5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942950"
---
# <a name="clearerr"></a>clearerr

Obnoví indikátor chyby pro datový proud. K dispozici je bezpečnější verze této funkce; viz [clearerr_s](clearerr-s.md).

## <a name="syntax"></a>Syntaxe

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="remarks"></a>Poznámky

Funkce **clearerr** resetuje indikátor chyby a indikátor konce souboru pro *datový proud*. Indikátory chyb nejsou automaticky vymazány. Jakmile je indikátor chyby pro zadaný datový proud nastavený, operace s tímto datovým proudem budou dál vracet chybovou hodnotu, dokud se nevolá **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**nebo [Rewind](rewind.md) .

Pokud má *datový proud* **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí. Další informace o **errno** a chybových kódech naleznete v tématu [konstanty errno](../../c-runtime-library/errno-constants.md).

K dispozici je bezpečnější verze této funkce; viz [clearerr_s](clearerr-s.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

### <a name="input"></a>Vstup

```Input
n
```

### <a name="output"></a>Výstup

```Output
Write error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>Viz také:

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
