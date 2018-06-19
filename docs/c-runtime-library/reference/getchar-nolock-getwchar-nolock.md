---
title: _getchar_nolock –, _getwchar_nolock – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getchar_nolock
- _getwchar_nolock
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
apitype: DLLExport
f1_keywords:
- getwchar_nolock
- _getwchar_nolock
- _getchar_nolock
- getchar_nolock
dev_langs:
- C++
helpviewer_keywords:
- _getwchar_nolock function
- getwchar_nolock function
- characters, reading
- _getchar_nolock function
- getchar_nolock function
- standard input, reading from
ms.assetid: dc49ba60-0647-4ae9-aa9a-a0618b1666de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83388f8c8d1788fa42f193030a45bf97c3472e23
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400395"
---
# <a name="getcharnolock-getwcharnolock"></a>_getchar_nolock, _getwchar_nolock

Čte znak z standardní vstup.

## <a name="syntax"></a>Syntaxe

```C
int _getchar_nolock( void );
wint_t _getwchar_nolock( void );
```

## <a name="return-value"></a>Návratová hodnota

V tématu [getchar getwchar –](getchar-getwchar.md).

## <a name="remarks"></a>Poznámky

**_getchar_nolock –** a **_getwchar_nolock –** jsou stejné jako **getchar** a **getwchar –** s tím rozdílem, že nejsou chráněny před narušení jiná vláken. Může být rychlejší, protože nevznikají nároky na uzamčení jiná vlákna. Tyto funkce lze používejte pouze v kontextu vláken jako je například aplikace nebo kde oboru volání již zpracovává izolace přístup z více vláken.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettchar_nolock**|**_getchar_nolock**|**_getchar_nolock**|**_getwchar_nolock**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getchar_nolock**|\<stdio.h>|
|**_getwchar_nolock**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getchar_nolock.c
// Use _getchar_nolock to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = _getchar_nolock()) != EOF)
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

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
