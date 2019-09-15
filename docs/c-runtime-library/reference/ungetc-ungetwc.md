---
title: ungetc, ungetwc
ms.date: 11/04/2016
api_name:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: f3b6c6ed3fe8ff5976afa1da2ed437e25c923b99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957421"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Posune znak zpět do datového proudu.

## <a name="syntax"></a>Syntaxe

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak, který má být vložen.

*stream*<br/>
Ukazatel na strukturu **souborů** .

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu každá z těchto funkcí vrátí argument znaků *c*. Pokud *c* nelze vrátit zpět nebo pokud nebyl načten žádný znak, vstupní datový proud se nezměnil a **ungetc –** vrátí **EOF**. **ungetwc** vrátí **WEOF**. Pokud má *datový proud* **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí znak **EOF** nebo **WEOF** a **errno** je nastaven na hodnotu **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **ungetc –** vloží znak *c* zpět do *datového proudu* a vymaže indikátor konce souboru. Datový proud musí být otevřen pro čtení. Následná operace čtení na *Stream* začíná na *c*. Pokus o vložení **EOF** do streamu pomocí **ungetc –** se ignoruje.

Znaky, které jsou umístěny na datový proud by **ungetc –** , mohou být smazány, pokud je volána metoda **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**nebo [Rewind](rewind.md) před čtením znaku z datového proudu. Indikátor pozice v souboru bude mít hodnotu, kterou měl předtím, než se znaky posunuly zpátky. Externí úložiště odpovídající datovému proudu je beze změny. Po úspěšném volání **ungetc –** proti textovému datovému proudu je indikátor pozice v souboru neurčen, dokud nebudou všechny znaky pro vložení zpět čteny nebo zahozeny. Při každém úspěšném volání **ungetc –** proti binárnímu proudu je indikátor pozice v souboru snížen; Pokud jeho hodnota byla 0 před voláním, hodnota není definována po volání.

Výsledky jsou nepředvídatelné, pokud je **ungetc –** volán dvakrát bez operace čtení nebo umístění souborů mezi dvěma voláními. Po volání **Fscanf**může volání **ungetc –** selhat, pokud není provedena jiná operace čtení (například **getc –** ). Důvodem je to, že **Fscanf** sám volá **ungetc –** .

**ungetwc** je verze **ungetc –** s velkým znakem. U každého úspěšného volání **ungetwc** proti textovému nebo binárnímu proudu však není hodnota indikátoru pozice v souboru zadána, dokud nejsou všechny znaky předaných zpět čteny nebo zahozeny.

Tyto funkce jsou bezpečné pro přístup z více vláken a při provádění se zamkne citlivá data. Neuzamykání verze naleznete v tématu [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc –**|**ungetc –**|**ungetwc**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ungetc –**|\<stdio.h>|
|**ungetwc**|\<stdio. h > nebo \<WCHAR. h >|

Konzola není v aplikacích Univerzální platforma Windows (UWP) podporována. Standardní popisovače streamů, které jsou spojeny s konzolou, **stdin**, **stdout**a **stderr**, musí být přesměrované před tím, než je funkce modulu runtime jazyka C můžou použít v aplikacích pro UWP. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>Viz také:

[Vstup/výstup datového proudu](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
