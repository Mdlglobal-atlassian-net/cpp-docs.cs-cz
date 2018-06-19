---
title: gets_s –, _getws_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getws_s
- gets_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getws_s
- gets_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3a5047871937d96288798768e17618ab791c75e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401815"
---
# <a name="getss-getwss"></a>gets_s, _getws_s

Získá řádek z **stdin –** datového proudu. Tyto verze nástroje [získá _getws –](../../c-runtime-library/gets-getws.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Vyrovnávací paměti*<br/>
Umístění úložiště pro vstupní řetězec.

*sizeInCharacters*<br/>
Velikost vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Vrátí *vyrovnávací paměti* v případě úspěchu. A **NULL** ukazatel označuje podmínku chyby nebo end souboru. Použití [ferror –](ferror.md) nebo [feof –](feof.md) k určení, které z nich došlo k chybě.

## <a name="remarks"></a>Poznámky

**Gets_s –** funkce přečte řádek z standardní vstupní proud **stdin –** a uloží jej do *vyrovnávací paměti*. Tento řádek představuje všechny znaky do a včetně první znak nového řádku (\n). **gets_s –** pak nahradí znak nového řádku znak hodnoty null (\0) před vrácením řádku. Naproti tomu **fgets_s** funkce uchovává znak nového řádku.

Pokud je první znak číst znak end souboru, prázdný znak je uložený na začátku *vyrovnávací paměti* a **NULL** je vrácen.

**_getws_s –** je verze široká charakterová **gets_s –**; její argument a návratové hodnoty jsou široká charakterová řetězce.

Pokud *vyrovnávací paměti* je **NULL** nebo *sizeInCharacters* je menší než nebo rovna nule, nebo pokud vyrovnávací paměť je příliš malá, aby obsahovat vstupní řádku a null ukončovací znak, tyto funkce vyvolání Neplatný parametr rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **NULL** a nastavte errno na **erange –**.

V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s –**|**gets_s –**|**_getws_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**gets_s –**|\<stdio.h>|
|**_getws_s**|\<stdio.h > nebo \<wchar.h >|

Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, **stdin –**, **stdout**, a **stderr**, musí být přesměrována C běhové funkce mohli používat v aplikacích pro UPW . Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
