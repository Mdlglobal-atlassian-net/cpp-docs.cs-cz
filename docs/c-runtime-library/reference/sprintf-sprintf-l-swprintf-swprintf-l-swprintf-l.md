---
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
ms.date: 11/04/2016
api_name:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: c9a306788045fc6fe52da835029d32cfc42c0ed4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958292"
---
# <a name="sprintf-_sprintf_l-swprintf-_swprintf_l-__swprintf_l"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

Zápis formátovaných dat do řetězce. K dispozici jsou bezpečnější verze některých z těchto funkcí; viz [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Zabezpečené verze **swprintf** a **_swprintf_l** nevezmou parametr *Count* .

## <a name="syntax"></a>Syntaxe

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Umístění úložiště pro výstup

*výpočtu*<br/>
Maximální počet znaků, které mají být uloženy ve verzi Unicode této funkce.

*format*<br/>
Řetězec řízení formátu

*argument*<br/>
Nepovinné argumenty

*jazyka*<br/>
Národní prostředí, které se má použít

Další informace najdete v tématu [specifikace formátu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Návratová hodnota

Počet zapsaných znaků nebo hodnota-1, pokud došlo k chybě. Pokud je *vyrovnávací paměť* nebo *Formát* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

**sprintf –** vrací počet bajtů uložených v *bufferu*a nepočítá ukončující znak null. **swprintf** vrací počet velkých znaků uložených v *bufferu*a nepočítá ukončující znak null.

## <a name="remarks"></a>Poznámky

Funkce **sprintf –** formátuje a ukládá řadu znaků a hodnot v *bufferu*. Každý *argument* (pokud existuje) je převeden a výstup podle odpovídající specifikace formátu ve *formátu*. Formát se skládá z běžných znaků a má stejnou formu a funkci jako argument *Format* pro [printf](printf-printf-l-wprintf-wprintf-l.md). Po napsání posledního znaku je připojen znak null. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

> [!IMPORTANT]
> Pomocí **sprintf –** neexistuje žádný způsob, jak omezit počet zapsaných znaků, což znamená, že kód používající **sprintf –** je náchylný k přetečení vyrovnávací paměti. Zvažte použití související funkce [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), která určuje maximální počet znaků, které mají být zapsány do *vyrovnávací paměti*, nebo použijte [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) k určení, jak velká je požadovaná vyrovnávací paměť. Také se ujistěte, že *Formát* není uživatelem definovaný řetězec.

**swprintf** je **sprintf –** verze s velkým znakem; argumenty ukazatele na **swprintf** jsou řetězce s velkým znakem. Detekce chyb kódování v **swprintf** se může lišit od v **sprintf –** . **swprintf** a **fwprintf** se chovají stejně, s tím rozdílem, že **swprintf** zapisuje výstup do řetězce, nikoli do cíle typu **soubor**a **swprintf** vyžaduje, aby parametr *Count* určoval maximální počet. znaků, které mají být zapsány. Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

**swprintf** odpovídá standardu ISO C, který vyžaduje druhý parametr *Count*typu **size_t**. Chcete-li vynutit staré nestandardní chování, definujte **_CRT_NON_CONFORMING_SWPRINTFS**. V budoucí verzi je možné odebrat staré chování, takže by měl být kód změněn tak, aby používal nové vyhovující chování.

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**sprintf**, **_sprintf_l**|\<stdio.h>|
|**swprintf**, **_swprintf_l**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
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
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
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
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf – funkce](../../c-runtime-library/vprintf-functions.md)<br/>
