---
title: gets_s, _getws_s
ms.date: 11/04/2016
api_name:
- _getws_s
- gets_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getws_s
- gets_s
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
ms.openlocfilehash: f282b4e8de12185a19e07374cf565788dc549136
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954973"
---
# <a name="gets_s-_getws_s"></a>gets_s, _getws_s

Získá řádek ze streamu **stdin** . Tyto verze aplikace [_getws](../../c-runtime-library/gets-getws.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Umístění úložiště pro vstupní řetězec.

*sizeInCharacters*<br/>
Velikost vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí *do vyrovnávací paměti* . Ukazatel s **hodnotou null** indikuje stav chyby nebo konce souboru. K určení, která z nich se stala, použijte [trajekt](ferror.md) nebo [feof](feof.md) .

## <a name="remarks"></a>Poznámky

Funkce **gets_s** čte řádek ze standardního vstupního streamu **stdin** a ukládá ho do *vyrovnávací paměti*. Řádek se skládá ze všech znaků až do a včetně prvního znaku nového řádku (' \n '). **gets_s** pak před vrácením řádku nahradí znak nového řádku znakem null (' \ 0 '). Naproti tomu funkce **fgets_s** zachová znak nového řádku.

Pokud je první přečtený znak znakem konce souboru, je na začátku *vyrovnávací paměti* uložen znak null a je vrácena **hodnota null** .

**_getws_s** je **gets_s**verze s velkým znakem; jeho argument a návratová hodnota jsou řetězce s velkým znakem.

Pokud má *vyrovnávací paměť* **hodnotu null** nebo je *sizeInCharacters* menší nebo rovna nule nebo pokud je vyrovnávací paměť příliš malá pro vložení vstupního řádku a ukončovacího znaku null, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [parametru. Ověřování](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **hodnotu null** a nastaví errno na **ERANGE**.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio. h > nebo \<WCHAR. h >|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
