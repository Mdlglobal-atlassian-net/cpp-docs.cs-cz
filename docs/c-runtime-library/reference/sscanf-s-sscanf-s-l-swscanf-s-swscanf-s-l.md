---
title: sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
ms.date: 11/04/2016
api_name:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: 14707b64a9c5c49837391be59d83ee39b79d5065
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957970"
---
# <a name="sscanf_s-_sscanf_s_l-swscanf_s-_swscanf_s_l"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

Přečte formátovaná data z řetězce. Tyto verze [sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Uložená data

*format*<br/>
Řetězec řízení formátu Další informace najdete v tématu [formátování pole Specifikace: scanf a wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*argument*<br/>
Nepovinné argumenty

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí počet polí, která jsou úspěšně převedena a přiřazena; Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Návratová hodnota je znak **EOF** pro chybu, nebo pokud je dosaženo konce řetězce před prvním převodem.

Pokud je *vyrovnávací paměť* nebo *Formát* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL** .

Informace o těchto a dalších chybových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **sscanf_s** čte data z *vyrovnávací paměti* do umístění, které je zadáno každým *argumentem*. Argumenty za formátovacím řetězcem určují ukazatele na proměnné, které mají typ odpovídající specifikátoru typu ve *formátu*. Na rozdíl od méně bezpečné verze [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md)je vyžadován parametr velikosti vyrovnávací paměti, pokud použijete pole typ znaky **c**, **c**, **s**, **s**nebo sady řízení řetězce, které jsou uzavřeny v **[]** . Velikost vyrovnávací paměti ve znacích se musí zadat jako další parametr hned za parametrem vyrovnávací paměti, který to vyžaduje. Například pokud čtete do řetězce, je velikost vyrovnávací paměti tohoto řetězce předána následujícím způsobem:

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

Velikost vyrovnávací paměti zahrnuje ukončující hodnotu null. Pole Specifikace šířky se dá použít k zajištění toho, že token, který je čten v, se vejde do vyrovnávací paměti. Pokud není použito pole Specifikace šířky a token načtený v je příliš velký, aby se vešel do vyrovnávací paměti, do této vyrovnávací paměti se nezapisuje žádné informace.

V případě znaků může být jeden znak čten následujícím způsobem:

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

Tento příklad přečte jeden znak ze vstupního řetězce a pak ho uloží do vyrovnávací paměti s velkým znakem. Při čtení více znaků pro ukončené řetězce, které nejsou null, jsou použita celá čísla bez znaménka jako specifikace šířky a velikost vyrovnávací paměti.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Další informace naleznete v tématu [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) a [scanf Type Characters Field](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr size je typu **bez znaménka**, nikoli **size_t**. Při kompilaci pro 64 cíle použijte statické přetypování pro převod výsledků **_countof** nebo **sizeof** na správnou velikost.

Argument *Format* řídí interpretaci vstupních polí a má stejnou formu a funkci jako argument *Format* pro funkci **scanf_s** . Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

**swscanf_s** je **sscanf_s**verze s velkým znakem; argumenty **swscanf_s** jsou řetězce s libovolným znakem. **sscanf_s** nezpracovává vícebajtové šestnáctkové znaky. **swscanf_s** nezpracovává šestnáctkové znaky Unicode s plnou šířkou nebo "zónu kompatibility". V opačném případě se **swscanf_s** a **sscanf_s** chovají stejně.

Verze těchto funkcí, které mají příponu **_l** , jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**sscanf_s**, **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**, **_swscanf_s_l**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
