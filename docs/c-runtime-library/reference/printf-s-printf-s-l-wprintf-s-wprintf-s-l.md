---
title: printf_s, _printf_s_l, wprintf_s, _wprintf_s_l
ms.date: 11/04/2016
api_name:
- _printf_s_l
- wprintf_s
- _wprintf_s_l
- printf_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wprintf_s
- printf_s
helpviewer_keywords:
- wprintf_s function
- tprintf_s function
- _tprintf_s function
- printf_s_l function
- printf_s function
- _printf_s_l function
- printf function, format specification fields
- printf function, using
- _tprintf_s_l function
- wprintf_s_l function
- formatted text [C++]
- tprintf_s_l function
- _wprintf_s_l function
ms.assetid: 044ebb2e-5cc1-445d-bb4c-f084b405615b
ms.openlocfilehash: f8b324b5f3c23b324bdcd43e3529ad3a3d4d6847
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950186"
---
# <a name="printf_s-_printf_s_l-wprintf_s-_wprintf_s_l"></a>printf_s, _printf_s_l, wprintf_s, _wprintf_s_l

Vytiskne formátovaný výstup do standardního výstupního proudu. Tyto verze [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int printf_s(
   const char *format [,
   argument]...
);
int _printf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf_s(
   const wchar_t *format [,
   argument]...
);
int _wprintf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Parametry

*format*<br/>
Ovládací prvek Format

*argument*<br/>
Volitelné argumenty

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet vytištěných znaků nebo zápornou hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **printf_s** formátuje a tiskne řadu znaků a hodnot do standardního výstupního proudu **stdout**. Pokud argumenty následují *formátovací* řetězec, *formátovací* řetězec musí obsahovat specifikace, které určují výstupní formát argumentů.

Hlavní rozdíl mezi **printf_s** a **printf** je, že **printf_s** kontroluje řetězce formátu pro platné formátovací znaky, zatímco **printf** pouze kontroluje, zda je řetězec formátu ukazatel s hodnotou null. Pokud některá z těchto kontrol selžou, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Informace o **errno** a chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**printf_s** a **fprintf_s** se chovají stejně, s výjimkou toho, že **printf_s** zapisuje výstup do **stdout** místo do cíle typu **File**. Další informace najdete v tématu [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

**wprintf_s** je **printf_s**verze s velkým znakem; *Formát* je řetězec s velkým znakem. **wprintf_s** a **printf_s** se chovají stejně, pokud je datový proud otevřen v režimu ANSI. **printf_s** v současné době nepodporuje výstup do datového proudu Unicode.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE – definice|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf_s**|**printf_s**|**printf_s**|**wprintf_s**|
|**_tprintf_s_l**|**_printf_s_l**|**_printf_s_l**|**_wprintf_s_l**|

Argument *formátu* se skládá z běžných znaků, řídicích sekvencí a ( *Pokud následují argumenty formátu)* . Běžné znaky a řídicí sekvence jsou zkopírovány do **stdout** v pořadí podle jejich vzhledu. Například řádek

```C
printf_s("Line one\n\t\tLine two\n");
```

Vytvoří výstup

```Output
Line one
        Line two
```

[Specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) vždy začínají znakem procenta ( **%** ) a jsou čteny zleva doprava. Když **printf_s** narazí na první specifikaci formátu (pokud existuje), převede hodnotu prvního argumentu po jeho *formátování* a provede odpovídající výstup. Druhá specifikace formátu způsobí, že druhý argument bude převeden a výstup a tak dále. Pokud existuje více argumentů, než je specifikace formátu, nadbytečné argumenty jsou ignorovány. Pokud není dostatek argumentů pro všechny specifikace formátu, jsou výsledky nedefinovány.

> [!IMPORTANT]
> Ujistěte se, že *Formát* není uživatelem definovaný řetězec.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**printf_s**, **_printf_s_l**|\<stdio.h>|
|**wprintf_s**, **_wprintf_s_l**|\<stdio. h > nebo \<WCHAR. h >|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_printf_s.c
/* This program uses the printf_s and wprintf_s functions
* to produce formatted output.
*/

#include <stdio.h>

int main( void )
{
   char   ch = 'h', *string = "computer";
   int    count = -9234;
   double fp = 251.7366;
   wchar_t wch = L'w', *wstring = L"Unicode";

   /* Display integers. */
   printf_s( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  Unsigned: %u\n",
           count, count, count );

   printf_s( "Decimal %d as:\n   Hex: %Xh  C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   /* Display in different radixes. */
   printf_s( "Digits 10 equal:\n   Hex: %i  Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   /* Display characters. */

   printf_s("Characters in field (1):\n%10c%5hc%5C%5lc\n", ch, ch, wch, wch);
   wprintf_s(L"Characters in field (2):\n%10C%5hc%5c%5lc\n", ch, ch, wch, wch);

   /* Display strings. */

   printf_s("Strings in field (1):\n%25s\n%25.4hs\n   %S%25.3ls\n",
   string, string, wstring, wstring);
   wprintf_s(L"Strings in field (2):\n%25S\n%25.4hs\n   %s%25.3ls\n",
       string, string, wstring, wstring);

   /* Display real numbers. */
   printf_s( "Real numbers:\n   %f %.2f %e %E\n", fp, fp, fp, fp );

   /* Display pointer. */
   printf_s( "\nAddress as:   %p\n", &count);

}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF78
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
