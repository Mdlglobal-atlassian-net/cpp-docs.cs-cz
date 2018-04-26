---
title: printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f47a7c10b870ed6ecc4d882a585e335c8c93ac4f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="printfs-printfsl-wprintfs-wprintfsl"></a>printf_s, _printf_s_l, wprintf_s, _wprintf_s_l

Výstup do standardního výstupního datového proudu ve formátu výtisků. Tyto verze nástroje [printf _printf_l –, wprintf, _wprintf_l –](printf-printf-l-wprintf-wprintf-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Formát ovládacího prvku.

*Argument*<br/>
Volitelné argumenty

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí počet znaků, vytisknout nebo záporná, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

**Printf_s –** funkce naformátuje a vytiskne řady znaků a hodnot do standardního výstupního datového proudu **stdout**. Pokud argumenty postupovat podle *formátu* řetězce, *formát* řetězec musí obsahovat specifikace, které určují formát výstupu pro argumenty.

Hlavní rozdíl mezi **printf_s –** a **printf** je, že **printf_s –** ověří řetězec formátu pro formátování platné znaky, zatímco **printf**  pouze ověří, zda je řetězec formátu ukazatele null. Pokud buď kontrola selže, je obslužnou rutinu neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu -1 a nastaví je povoleno spuštění **errno** k **einval –**.

Informace o **errno** a kódy chyb, najdete v části [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**printf_s –** a **fprintf_s –** vyjma toho, že se chovají stejně jako **printf_s –** zapíše výstup do **stdout** spíše než do cílového umístění v typu **Soubor**. Další informace najdete v tématu [fprintf_s –, _fprintf_s_l –, fwprintf_s –, _fwprintf_s_l –](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

**wprintf_s –** je verze široká charakterová **printf_s –**; *formát* je široká charakterová řetězec. **wprintf_s –** a **printf_s –** chovají stejně jako datový proud se při otevření v režimu ANSI. **printf_s –** nepodporuje aktuálně výstup do proudu kódování UNICODE.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definované|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf_s –**|**printf_s**|**printf_s**|**wprintf_s**|
|**_tprintf_s_l –**|**_printf_s_l**|**_printf_s_l**|**_wprintf_s_l**|

*Formátu* argument obsahuje obyčejnou znaky, řídicí sekvence, a (Pokud postupovat podle argumenty *formát*) specifikace formátu. Obyčejnou znaků a řídicích sekvencí se zkopírují do **stdout** v pořadí podle jejich vzhled. Například řádek

```C
printf_s("Line one\n\t\tLine two\n");
```

Vytvoří výstup

```Output
Line one
        Line two
```

[Specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) vždy začínat znakem procent (**%**) a jsou přečteny vlevo, vpravo. Když **printf_s –** zaznamená první specifikace formátu (pokud existuje), převede ji hodnotu po první argument *formátu* a uloží jej odpovídajícím způsobem. Druhý specifikace formátu způsobí, že aby druhý argument nutné převést a výstup, a tak dále. Pokud existují další argumenty, než je specifikace formátu, další argumenty jsou ignorovány. Výsledky nejsou definovány, pokud nejsou k dispozici dostatečný počet argumentů pro všechny specifikace formátu.

> [!IMPORTANT]
> Ujistěte se, že *formát* není řetězec definovaný uživatelem.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**printf_s –**, **_printf_s_l –**|\<stdio.h>|
|**wprintf_s –**, **_wprintf_s_l –**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
