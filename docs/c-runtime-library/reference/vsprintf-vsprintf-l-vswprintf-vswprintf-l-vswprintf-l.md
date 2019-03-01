---
title: vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, __vswprintf_l
ms.date: 11/04/2016
apiname:
- _vswprintf_l
- _vsprintf_l
- vsprintf
- vswprintf
- __vswprintf_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- vstprintf
- vswprintf
- _vstprintf
- vsprintf
- __vswprintf_l
- _vsprintf_l
- _vswprintf_l
- vswprintf_l
helpviewer_keywords:
- __vswprintf_l function
- _vstprintf_l function
- formatted text
- vstprintf_l function
- _vswprintf_l function
- vsprintf_l function
- buffers, avoiding overruns
- buffer overruns
- vswprintf_l function
- buffers, buffer overruns
- vstprintf function
- _vsprintf_l function
- vswprintf function
- vsprintf function
- _vstprintf function
ms.assetid: b8ef1c0d-58f9-4a18-841a-f1a989e1c29b
ms.openlocfilehash: 4b6dd55f90a3766dc250040e27b80f9b1c64fde3
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210325"
---
# <a name="vsprintf-vsprintfl-vswprintf-vswprintfl-vswprintfl"></a>vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, __vswprintf_l

Zapíše formátovaný výstup pomocí ukazatele na seznam argumentů. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [vsprintf_s – _vsprintf_s_l –, vswprintf_s – _vswprintf_s_l –](vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int vsprintf(
   char *buffer,
   const char *format,
   va_list argptr
);
int _vsprintf_l(
   char *buffer,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vswprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vswprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
int __vswprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsprintf(
   char (&buffer)[size],
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int vswprintf(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vswprintf_l(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro výstup.

*Počet*<br/>
Maximální počet znaků k uložení širokého řetězce verze této funkce.

*Formát*<br/>
Specifikace formátu.

*argptr*<br/>
Ukazatel na seznam argumentů.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**vsprintf –** a **vswprintf –** vrátí počet napsaných znaků, nikoli včetně ukončujícího znaku null, nebo zápornou hodnotu, pokud dojde k chybě výstupu. Pokud *vyrovnávací paměti* nebo *formátu* je ukazatel s hodnotou null, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí bere ukazatel na seznam argumentů a potom formátuje a zapisuje poskytnutá data do paměti, na které odkazuje *vyrovnávací paměti*.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí předaného namísto aktuálního národní prostředí pro vlákno.

> [!IMPORTANT]
> Pomocí **vsprintf –**, že se žádný způsob, jak omezit počet znaků zapsaných, což znamená, že kód pomocí této funkce je náchylný k přetečení vyrovnávací paměti. Použití [_vsnprintf –](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) místo, nebo se telefonicky [_vscprintf –](vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md) k určení, jak velkou vyrovnávací paměť je potřeba. Také se ujistěte, že *formátu* není uživatelem definovaný řetězec. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

**vswprintf –** odpovídá standardu ISO C, který vyžaduje druhý parametr, *počet*, typu **size_t**. K vynucení starého nestandardního chování definujte **_CRT_NON_CONFORMING_SWPRINTFS**. Staré chování nemusí být v budoucí verzi, takže kód by měl změnit používat nové chování splňující podmínky.

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstprintf**|**vsprintf**|**vsprintf**|**vswprintf**|
|**_vstprintf_l**|**_vsprintf_l**|**_vsprintf_l**|**_vswprintf_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**vsprintf**, **_vsprintf_l**|\<stdio.h > a \<stdarg.h >|\<varargs.h>*|
|**vswprintf**, **_vswprintf_l**|\<stdio.h > nebo \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Vyžaduje se pro kompatibility systému UNIX V.

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_vsprintf.c
// compile with: /W3
// This program uses vsprintf to write to a buffer.
// The size of the buffer is determined by _vscprintf.

#include <stdlib.h>
#include <stdio.h>
#include <stdarg.h>

void test( char * format, ... )
{
    va_list args;
    int     len;
    char    *buffer;

    // retrieve the variable arguments
    va_start( args, format );

    len = _vscprintf( format, args ) // _vscprintf doesn't count
                                + 1; // terminating '\0'

    buffer = (char*)malloc( len * sizeof(char) );

    vsprintf( buffer, format, args ); // C4996
    // Note: vsprintf is deprecated; consider using vsprintf_s instead
    puts( buffer );

    free( buffer );
    va_end( args );
}

int main( void )
{
   test( "%d %c %d", 123, '<', 456 );
   test( "%s", "This is a string" );
}
```

```Output
123 < 456
This is a string
```

## <a name="see-also"></a>Viz také:

[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
[Syntaxe specifikace formátu: funkce printf a wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
