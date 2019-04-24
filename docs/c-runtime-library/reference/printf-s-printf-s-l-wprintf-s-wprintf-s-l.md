---
title: printf_s, _printf_s_l, wprintf_s, _wprintf_s_l
ms.date: 11/04/2016
apiname:
- _printf_s_l
- wprintf_s
- _wprintf_s_l
- printf_s
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
ms.openlocfilehash: 6b07fd90e0390d5c39bc8f5885f5744de20eeb79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231998"
---
# <a name="printfs-printfsl-wprintfs-wprintfsl"></a>printf_s, _printf_s_l, wprintf_s, _wprintf_s_l

Tiskne formátovaný výstup do standardního výstupního datového proudu. Tyto verze [printf _printf_l –, wprintf _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Formát*<br/>
Formátování ovládacího prvku.

*argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet vytištěných znaků nebo záporná hodnota, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**Printf_s** funkce formátuje a vytiskne řadu znaků a hodnot do standardního výstupního datového proudu **stdout**. Pokud argumenty jsou podle *formátu* řetězce, *formátu* řetězec musí obsahovat specifikace, které určují požadovaný výstupní formát argumentů.

Hlavní rozdíl mezi **printf_s** a **printf** je, že **printf_s** kontroluje v řetězci formátování platnost znaků formátování, zatímco **printf**  pouze ověří, zda formátovací řetězec ukazatel s hodnotou null. Pokud kontrola selže, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

Informace o **errno** a kódy chyb, naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**printf_s** a **fprintf_s –** chovají stejně, s výjimkou, že **printf_s** zapíše výstup do **stdout** , nikoli do cílového umístění typu **Souboru**. Další informace najdete v tématu [fprintf_s – _fprintf_s_l –, fwprintf_s – _fwprintf_s_l –](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

**wprintf_s –** je verze širokého znaku **printf_s**; *formátu* je širokoznaký řetězec. **wprintf_s –** a **printf_s** chovají stejně jako v případě, že datový proud je otevřen v režimu ANSI. **printf_s** aktuálně nepodporuje výstup do datového proudu UNICODE.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí předaného namísto aktuálního národní prostředí pro vlákno.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf_s**|**printf_s**|**printf_s**|**wprintf_s**|
|**_tprintf_s_l**|**_printf_s_l**|**_printf_s_l**|**_wprintf_s_l**|

*Formátu* argument se skládá z běžných znaků, řídících sekvencí a (Pokud argumenty jsou podle *formátu*) specifikace formátu. Obyčejné znaky a sekvence escape se zkopírují do **stdout** v pořadí jejich výskytu. Například řádek

```C
printf_s("Line one\n\t\tLine two\n");
```

Vytvoří výstup

```Output
Line one
        Line two
```

[Specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) vždy začínají znakem procenta (**%**) a jsou čteny zleva doprava. Když **printf_s** nalezne první specifikaci formátu (pokud existuje), převede hodnotu prvního argumentu po *formátu* a uloží jej odpovídajícím způsobem. Druhá specifikace formátu způsobí, že druhý argument bude převeden a uložen, a tak dále. Pokud existuje více argumentů, než je specifikace formátu, další argumenty jsou ignorovány. Výsledky nejsou definovány, jestliže neexistuje dostatek argumentů pro všechny specifikace formátu.

> [!IMPORTANT]
> Ujistěte se, že *formátu* není uživatelem definovaný řetězec.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**printf_s**, **_printf_s_l**|\<stdio.h>|
|**wprintf_s**, **_wprintf_s_l**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UPW). Standardní datový proud popisovačů, které jsou spojeny s konzolou, **stdin**, **stdout**, a **stderr**, musí být přesměrován před funkcí jazyka C za běhu můžete použít v aplikacích pro UWP . Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
[Stream vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
