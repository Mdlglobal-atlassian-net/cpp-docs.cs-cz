---
title: _fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l
ms.date: 11/04/2016
apiname:
- _fwprintf_p
- _fprintf_p_l
- _fwprintf_p_l
- _fprintf_p
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
- _fprintf_p
- _ftprintf_p
- fwprintf_p
- _fwprintf_p
- fprintf_p
- ftprintf_p
helpviewer_keywords:
- fprintf_p_l function
- fprintf_p function
- _fprintf_p_l function
- _fprintf_p function
- _ftprintf_p_l function
- streams, printing formatted data to
- _fwprintf_p function
- fwprintf_p function
- _ftprintf_p function
- _fwprintf_p_l function
- ftprintf_p function
- printing [C++], formatted data to streams
- ftprintf_p_l function
- fwprintf_p_l function
ms.assetid: 46b082e1-45ba-4383-9ee4-97015aa50bc6
ms.openlocfilehash: db9e9a746193c7bf35913d6792d87aa9ba85fa79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462774"
---
# <a name="fprintfp-fprintfpl-fwprintfp-fwprintfpl"></a>_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l

Tisk formátovaných dat do datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int _fprintf_p(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fprintf_p_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int _fwprintf_p(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwprintf_p_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Ukazatel **souboru** struktury.

*Formát*<br/>
Řetězec řízení formátu

*Argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_fprintf_p –** a **_fwprintf_p –** vrátí počet napsaných znaků nebo vrátí zápornou hodnotu, když dojde k chybě výstupu.

## <a name="remarks"></a>Poznámky

**_fprintf_p –** formátuje a vytiskne řadu znaků a hodnot do výstupu *stream*. Každá funkce *argument* (pokud existuje) je převeden a uložen podle odpovídající specifikace formátu v *formátu*. Pro **_fprintf_p –**, *formátu* argument má stejnou syntaxi a použití, který má v **_printf_p –**. Tyto funkce podporuje poziční parametry, což znamená, že můžete změnit pořadí parametrů použitých ve formátovacím řetězci. Další informace o poziční parametry, naleznete v tématu [printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md).

**_fwprintf_p –** je verze širokého znaku **_fprintf_p –**; v **_fwprintf_p –**, *formátu* je širokoznaký řetězec. Tyto funkce chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **_fprintf_p –** aktuálně nepodporuje výstup do datového proudu UNICODE.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí namísto aktuálního národního prostředí předaného.

> [!IMPORTANT]
> Ujistěte se, že *formátu* není uživatelem definovaný řetězec.

Podobně jako nezabezpečené verze (viz [fprintf _fprintf_l –, fwprintf – _fwprintf_l –](fprintf-fprintf-l-fwprintf-fwprintf-l.md)), tyto funkce ověřují své parametry a vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md), pokud buď *stream* nebo *formátu* je ukazatel s hodnotou null, nebo pokud neexistují žádné neznámé nebo chybně zformulované formátovací specifikátory. Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_ftprintf_p –**|**_fprintf_p**|**_fprintf_p**|**_fwprintf_p**|
|**_ftprintf_p_l –**|**_fprintf_p_l**|**_fprintf_p_l**|**_fwprintf_p_l**|

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fprintf_p –**, **_fprintf_p_l –**|\<stdio.h>|
|**_fwprintf_p –**, **_fwprintf_p_l –**|\<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_fprintf_p.c
// This program uses _fprintf_p to format various
// data and print it to the file named FPRINTF_P.OUT. It
// then displays FPRINTF_P.OUT on the screen using the system
// function to invoke the operating-system TYPE command.
//

#include <stdio.h>
#include <process.h>

int main( void )
{
    FILE    *stream = NULL;
    int     i = 10;
    double  fp = 1.5;
    char    s[] = "this is a string";
    char    c = '\n';

    // Open the file
    if ( fopen_s( &stream, "fprintf_p.out", "w" ) == 0)
    {
        // Format and print data
        _fprintf_p( stream, "%2$s%1$c", c, s );
        _fprintf_p( stream, "%d\n", i );
        _fprintf_p( stream, "%f\n", fp );

        // Close the file
        fclose( stream );
    }

    // Verify our data
    system( "type fprintf_p.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf _sprintf_l –, swprintf, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)<br/>
[_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[printf_p – poziční parametry](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
