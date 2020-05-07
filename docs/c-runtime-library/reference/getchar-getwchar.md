---
title: getchar, getwchar
ms.date: 4/2/2020
api_name:
- getchar
- getwchar
- _o_getchar
- _o_getwchar
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
- getwchar
- GetChar
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
ms.openlocfilehash: 2073f23583772f71489f1597b0df8e1e6abe2253
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920333"
---
# <a name="getchar-getwchar"></a>getchar, getwchar

Přečte znak ze standardního vstupu.

## <a name="syntax"></a>Syntaxe

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>Návratová hodnota

Vrátí přečtený znak. Chcete-li indikovat chybu čtení nebo stav konce souboru, funkce **GetChar** vrátí znak **EOF**a **getwchar** vrátí hodnotu **WEOF**. V případě **GetChar**použijte k vyhledání chyby nebo konce souboru použití metody **trajekt** nebo **feof** .

## <a name="remarks"></a>Poznámky

Každá rutina přečte jeden znak ze **standardního vstupu** a zvýší přidružený ukazatel na soubor tak, aby odkazoval na další znak. **GetChar** je stejný jako [_fgetchar](fgetc-fgetwc.md), ale je implementován jako funkce a jako makro.

Tyto funkce zamkne volající vlákno a jsou proto bezpečná pro přístup z více vláken. Neuzamykání verze naleznete v tématu [_getchar_nolock _getwchar_nolock](getchar-nolock-getwchar-nolock.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**GetChar**|**GetChar**|**getwchar**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**GetChar**|\<stdio. h>|
|**getwchar**|\<stdio. h> nebo \<WCHAR. h>|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getchar.c
// Use getchar to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
