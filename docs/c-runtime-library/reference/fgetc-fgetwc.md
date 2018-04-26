---
title: fgetc –, fgetwc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fgetwc
- fgetc
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
- _fgettc
- fgetwc
- fgetc
dev_langs:
- C++
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82db726bc0296027536798771680cc1326fc00df
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Znak číst z datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktura.

## <a name="return-value"></a>Návratová hodnota

**fgetc –** vrátí znak přečíst jako **int** nebo vrátí **EOF** udávajících chyba nebo konec souboru. **fgetwc –** vrátí, jako [wint_t –](../../c-runtime-library/standard-types.md), široké znak, který odpovídá znak čtení nebo vrátí **weof –** udávajících chyba nebo konec souboru. Pro obě funkce použijte **feof –** nebo **ferror –** rozlišit mezi chybu a podmínku end souboru. Pokud dojde k chybě čtení, je nastavit označení chyb pro datový proud. Pokud *datového proudu* je **NULL**, **fgetc –** a **fgetwc –** vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátit **EOF**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí čte jeden znak z aktuální pozici soubor přidružený k *datového proudu*. Funkce pak zvýší přidružený soubor ukazatele (je-li definována) tak, aby odkazoval na další znak. Pokud datový proud je na konci souboru, je nastavit koncové souboru indikátor pro datový proud.

**fgetc –** je ekvivalentní **getc**, ale je implementována pouze jako funkci, nikoli jako funkce a makra.

**fgetwc –** je verze široká charakterová **fgetc –**; přečte **c** jako vícebajtových znaků nebo široká znaková podle jestli *datového proudu* je otevřen v režim textové nebo binárního režimu.

Verzi pomocí **jazyka _nolock** příponu jsou shodné s tím rozdílem, že nejsou chráněny z narušení jiná vlákna.

Další informace o zpracování široké znaky a více-bajtové znaky v textovém a binárním režimu najdete v tématu [vstupně-výstupní datový proud Unicode v textovém a binárním režimu](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc –**|**fgetc –**|**fgetc –**|**fgetwc –**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fgetc –**|\<stdio.h>|
|**fgetwc –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetctxt"></a>Vstup: crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
