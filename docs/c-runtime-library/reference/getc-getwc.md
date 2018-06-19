---
title: getc, getwc – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a4908e8fa3343bb54191fe2494f738ff0edf887
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404328"
---
# <a name="getc-getwc"></a>getc, getwc

Znak číst z datového proudu.

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

*Datový proud*<br/>
Vstupní datový proud.

## <a name="return-value"></a>Návratová hodnota

Vrátí znak pro čtení. K označení došlo k chybě nebo podmínku end souborového **getc** vrátí **EOF**, a **getwc –** vrátí **weof –**. Pro **getc**, použijte **ferror –** nebo **feof –** ke kontrole pro chybu nebo pro konec souboru. Pokud *datového proudu* je **NULL**, **getc** a **getwc –** vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **EOF** (nebo **weof –** pro **getwc –**) a nastavte **errno** k  **Einval –**.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších kódy chyb.

## <a name="remarks"></a>Poznámky

Každou rutinu přečte jednoho znaku ze souboru na aktuální pozici a zvýší přidružený soubor ukazatele (je-li definována) tak, aby odkazoval na další znak. Soubor je přidružen *datového proudu*.

Tyto funkce Uzamknout volající vlákno a proto jsou bezpečné pro přístup z více vláken. Bez uzamčení verze, najdete v části [_getc_nolock –, _getwc_nolock –](getc-nolock-getwc-nolock.md).

Postupujte podle konkrétní rutiny poznámky.

|Rutina|Poznámky|
|-------------|-------------|
|**getc**|Stejné jako **fgetc –**, ale implementovaná jako funkce a jako makra.|
|**getwc –**|Široká charakterová verzi **getc**. Čte vícebajtových znaků nebo široká znaková podle jestli *datového proudu* je otevřen v režimu textových nebo binárního režimu.|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc –**|**getc**|**getc**|**getwc –**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
