---
title: sprintf_s –, _sprintf_s_l –, swprintf_s –, _swprintf_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
dev_langs:
- C++
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0200740df3b41e356bcf83f0756b8a5267b38166
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417788"
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

Zápis formátovaná data na řetězec. Toto jsou verze [sprintf, _sprintf_l –, swprintf –, _swprintf_l –, \__swprintf_l –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro výstup

*sizeOfBuffer*<br/>
Maximální počet znaků, které se mají uložit

*Formát*<br/>
Řetězec formátu – ovládací prvek

*...*<br/>
Volitelné argumenty, které mají být ve formátu

*Národní prostředí*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

Počet znaků, které jsou zapsány nebo -1, pokud došlo k chybě. Pokud *vyrovnávací paměti* nebo *formátu* je ukazatel s hodnotou null, **sprintf_s –** a **swprintf_s –** vrátí hodnotu -1 a nastavte **errno**k **einval –**.

**sprintf_s –** vrátí počet bajtů, které jsou uložené v *vyrovnávací paměti*, není počítání ukončující znak hodnoty null. **swprintf_s –** vrátí počet široké znaky, které jsou uložené v *vyrovnávací paměti*, není počítání ukončující široká znaková hodnotu null.

## <a name="remarks"></a>Poznámky

**Sprintf_s –** funkce naformátuje a ukládá řady znaků a hodnot v *vyrovnávací paměti*. Každý *argument* (pokud existuje) je převeden a výstup podle odpovídající specifikaci formátu v *formátu*. Formát obsahuje obyčejnou znaky a má stejné tvoří a fungovat jako *formátu* argument pro [printf](printf-printf-l-wprintf-wprintf-l.md). Znak hodnoty null se připojí po poslední znak zapsána. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

Jeden hlavní rozdíl mezi **sprintf_s –** a [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) je, že **sprintf_s –** ověří řetězec formátu pro formátování platné znaky, zatímco [ sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) kontroluje pouze pokud jsou formátu řetězce nebo vyrovnávací paměti **NULL** ukazatele. Pokud buď kontrola selže, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, funkce vrátí hodnotu -1 a nastaví je povoleno spuštění **errno** k **einval –**.

Další hlavní rozdíl mezi **sprintf_s –** a [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) je, že **sprintf_s –** přebírá parametr délky ve znacích zadání velikost výstupní vyrovnávací paměť. Pokud vyrovnávací paměť je příliš malá pro formátovaný text, včetně ukončující null, pak vyrovnávací paměť je nastavena na prázdný řetězec umístěním znak hodnoty null v *vyrovnávací paměti*[0], a je volána obslužná rutina neplatný parametr. Na rozdíl od **_snprintf –**, **sprintf_s –** zaručuje, že vyrovnávací paměť bude null ukončena Pokud velikost vyrovnávací paměti je nulová.

**swprintf_s –** je verze široká charakterová **sprintf_s –**; ukazatel argumenty, které mají **swprintf_s –** jsou široká charakterová řetězce. Detekce chyb v kódování **swprintf_s –** se můžou lišit od v **sprintf_s –**. Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí vlákna.

V jazyce C++ těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení můžete odvození délka vyrovnávací paměti automaticky, takže není potřeba zadávat argumentem velikosti a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Existují verze **sprintf_s –** , které nabízejí další kontrolu nad co se stane, pokud vyrovnávací paměť je příliš malá. Další informace najdete v tématu [_snprintf_s –, _snprintf_s_l –, _snwprintf_s –, _snwprintf_s_l –](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s –**|**sprintf_s**|**sprintf_s**|**swprintf_s –**|
|**_stprintf_s_l –**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**sprintf_s –**, **_sprintf_s_l –**|C: \<stdio.h ><br /><br /> C++: \<cstdio – > nebo \<stdio.h >|
|**swprintf_s –**, **_swprintf_s_l –**|C: \<stdio.h > nebo \<wchar.h ><br /><br /> C++: \<cstdio – >, \<cwchar – >, \<stdio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>Příklad

```C
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
