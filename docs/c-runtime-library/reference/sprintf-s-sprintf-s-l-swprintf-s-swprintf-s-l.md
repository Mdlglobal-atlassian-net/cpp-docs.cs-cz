---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
ms.date: 11/04/2016
api_name:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
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
ms.openlocfilehash: 34b3ddce68563479b26abff34e8fa31f6298558a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958009"
---
# <a name="sprintf_s-_sprintf_s_l-swprintf_s-_swprintf_s_l"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

Zápis formátovaných dat do řetězce. Jedná se o verze [sprintf –, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*vyrovnávací paměti*<br/>
Umístění úložiště pro výstup

*sizeOfBuffer*<br/>
Maximální počet znaků, které se mají uložit

*format*<br/>
Řetězec řízení formátu

*...*<br/>
Volitelné argumenty, které mají být formátovány

*jazyka*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

Počet zapsaných znaků nebo hodnota-1, pokud došlo k chybě. Pokud je *vyrovnávací paměť* nebo *Formát* ukazatel s hodnotou null, **sprintf_s** a **swprintf_s** vrátí-1 a nastaví **errno** na **EINVAL**.

**sprintf_s** vrací počet bajtů uložených v *bufferu*a nepočítá ukončující znak null. **swprintf_s** vrací počet velkých znaků uložených v *bufferu*a nepočítá ukončující znak null.

## <a name="remarks"></a>Poznámky

Funkce **sprintf_s** formátuje a ukládá řadu znaků a hodnot v *bufferu*. Každý *argument* (pokud existuje) je převeden a výstup podle odpovídající specifikace formátu ve *formátu*. Formát se skládá z běžných znaků a má stejnou formu a funkci jako argument *Format* pro [printf](printf-printf-l-wprintf-wprintf-l.md). Po napsání posledního znaku je připojen znak null. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

Jedním z hlavních rozdílů mezi **sprintf_s** a [sprintf –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) je, že **sprintf_s** kontroluje řetězce formátu pro platné formátovací znaky, zatímco [sprintf –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) pouze kontroluje, zda je řetězec formátu nebo vyrovnávací paměť ukazateli s **hodnotou null** . Pokud některá z těchto kontrol selžou, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Druhým hlavním rozdílem mezi **sprintf_s** a [sprintf –](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) je, že **sprintf_s** přebírá parametr length, který určuje velikost výstupní vyrovnávací paměti ve znacích. Pokud je vyrovnávací paměť příliš malá pro formátovaný text, včetně ukončující hodnoty null, pak je vyrovnávací paměť nastavena na prázdný řetězec umístěním znaku null do *vyrovnávací paměti*[0] a je vyvolána obslužná rutina neplatného parametru. Na rozdíl od **_snprintf**zaručuje **sprintf_s** , že vyrovnávací paměť bude ukončena hodnotou null, pokud není velikost vyrovnávací paměti nulová.

**swprintf_s** je **sprintf_s**verze s velkým znakem; argumenty ukazatele na **swprintf_s** jsou řetězce s velkým znakem. Detekce chyb kódování v **swprintf_s** se může lišit od v **sprintf_s**. Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky, což eliminuje nutnost zadat argument Size a může automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Existují verze **sprintf_s** , které nabízejí další kontrolu nad tím, co se stane, pokud je vyrovnávací paměť příliš malá. Další informace najdete v tématu [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**sprintf_s**, **_sprintf_s_l**|C: \<stdio.h><br /><br /> C++: \<cstdio > nebo \<stdio. h >|
|**swprintf_s**, **_swprintf_s_l**|C: \<stdio. h > nebo \<WCHAR. h ><br /><br /> C++: \<cstdio >, \<cwchar >, \<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
