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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4311b5b896a5a406ebe14f09e7bb525cb47951b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344616"
---
# <a name="getchar-getwchar"></a>getchar, getwchar

Přečte znak ze standardního vstupu.

## <a name="syntax"></a>Syntaxe

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>Návratová hodnota

Vrátí přečtený znak. Chcete-li označit chybu čtení nebo podmínku konce souboru, **vrátí funkce getchar** **hodnotu EOF**a **funkce getwchar** vrátí **hodnotu WEOF**. Pro **getchar**, použijte **ferror** nebo **feof** zkontrolovat chybu nebo konec souboru.

## <a name="remarks"></a>Poznámky

Každá rutina přečte jeden znak z **stdin** a zvýrazní ukazatel přidruženého souboru tak, aby přecšlápne na další znak. **getchar** je stejný jako [_fgetchar](fgetc-fgetwc.md), ale je implementován jako funkce a jako makro.

Tyto funkce zamknout volající vlákno a jsou proto bezpečné pro přístup z více vláken. O verzi bez zamykání naleznete [v _getchar_nolock _getwchar_nolock](getchar-nolock-getwchar-nolock.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**getchar**|**getchar**|**getwchar**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**getchar**|\<stdio.h>|
|**getwchar**|\<stdio.h> \<nebo wchar.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke **konzole, stdin**, **stdout**a **stderr**, musí být přesměrovány před c run-time funkce je možné použít v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
