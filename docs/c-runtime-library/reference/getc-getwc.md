---
title: getc, getwc
ms.date: 11/04/2016
apiname:
- getwc
- getc
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
- _gettc
- getwc
- _gettchar
- getc
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
ms.openlocfilehash: bbaee79eac6802959a11f7f1ba30eaf590ecf2f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664864"
---
# <a name="getc-getwc"></a>getc, getwc

Čtení znaku z datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int getc(
   FILE *stream
);
wint_t getwc(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Vstupní datový proud.

## <a name="return-value"></a>Návratová hodnota

Vrátí čtení znaku. K označení chyby čtení nebo stavu ukončení souboru **getc** vrátí **EOF**, a **getwc –** vrátí **WEOF**. Pro **getc**, použijte **ferror** nebo **feof** zkontrolovat chybu nebo konec souboru. Pokud *stream* je **NULL**, **getc** a **getwc –** vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** (nebo **WEOF** pro **getwc –**) a nastavte **errno** k  **EINVAL**.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších chybových kódech.

## <a name="remarks"></a>Poznámky

Každá rutina načte jeden znak ze souboru na aktuální pozici a zvýší přidružený ukazatel na soubor (je-li definován) tak, aby odkazoval na další znak. Soubor je přidružený *stream*.

Tyto funkce uzamykají volající vlákno a proto jsou vláknově bezpečné. Nezamykací verzi naleznete v tématu [_getc_nolock – _getwc_nolock –](getc-nolock-getwc-nolock.md).

Následují poznámky specifické pro rutinu.

|Rutina|Poznámky|
|-------------|-------------|
|**getc**|Stejné jako **fgetc –**, ale implementovaná jako funkce a jako makro.|
|**getwc –**|Širokoznaká verze **getc**. Přečte vícebajtový znak nebo široký znak podle toho, zda *stream* je otevřen v textovém nebo binárním režimu.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc –**|**getc**|**getc**|**getwc –**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getc.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc.txt".

    fopen_s(&fp, "crt_getc.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crtgetctxt"></a>Vstup: crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Input was: Line one.
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
