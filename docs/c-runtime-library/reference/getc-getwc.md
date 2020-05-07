---
title: getc, getwc
ms.date: 4/2/2020
api_name:
- getwc
- getc
- _o_getc
- _o_getwc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 6248dd2287b2f11db72f64df1241affe8deec22d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919651"
---
# <a name="getc-getwc"></a>getc, getwc

Načtení znaku z datového proudu.

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

Vrátí přečtený znak. Pro indikaci chyby čtení nebo stavu konce souboru **getc –** vrátí **EOF**a **getwc** vrátí **WEOF**. Pro **getc –** použijte k vyhledání chyby nebo konce souboru použití nástroje pro **odvození** nebo **feof** . Pokud má *datový proud* **hodnotu null**, **getc –** a **getwc** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** (nebo **WEOF** pro **getwc**) a nastaví **errno** na **EINVAL**.

Další informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Každá rutina čte jeden znak ze souboru na aktuální pozici a zvýší přidružený ukazatel na soubor (je-li definován), aby ukazoval na další znak. Soubor je přidružen ke *streamu*.

Tyto funkce zamkne volající vlákno a jsou proto bezpečná pro přístup z více vláken. Neuzamykání verze naleznete v tématu [_getc_nolock _getwc_nolock](getc-nolock-getwc-nolock.md).

Následují poznámky specifické pro rutiny.

|Rutina|Poznámky|
|-------------|-------------|
|**getc –**|Stejné jako **fgetc**, ale implementované jako funkce a jako makro.|
|**getwc**|Verze **getc –** pro nejrůznější znaky. Přečte vícebajtový znak nebo velký znak podle toho, zda je *datový proud* otevřen v textovém režimu nebo v binárním režimu.|

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc**|**getc –**|**getc –**|**getwc**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getc –**|\<stdio. h>|
|**getwc**|\<stdio. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_getctxt"></a>Vstup: crt_getc. txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Výstup

```Output
Input was: Line one.
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
