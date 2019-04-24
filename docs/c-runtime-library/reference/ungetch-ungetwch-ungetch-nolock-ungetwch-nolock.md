---
title: _ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock
ms.date: 11/04/2016
apiname:
- _ungetch_nolock
- _ungetwch_nolock
- _ungetwch
- _ungetch
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ungetch_nolock
- ungetwch
- ungetch_nolock
- _ungetwch
- ungetch
- ungetwch_nolock
- _ungetch
- _ungettch_nolock
- _ungettch
- _ungetwch_nolock
helpviewer_keywords:
- _ungetch function
- ungetwch function
- characters, pushing back to console
- _ungettch_nolock function
- ungettch function
- _ungettch function
- ungetch_nolock function
- ungettch_nolock function
- _ungetwch_nolock function
- _ungetch_nolock function
- ungetwch_nolock function
- _ungetwch function
ms.assetid: 70ae71c6-228c-4883-a57d-de6d5f873825
ms.openlocfilehash: 7407d26606bd5242c430961faa4f60090b83f036
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268868"
---
# <a name="ungetch-ungetwch-ungetchnolock-ungetwchnolock"></a>_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock

Posune zpět poslední znak, který je přečten z konzoly.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ungetch(
   int c
);
wint_t _ungetwch(
   wint_t c
);
int _ungetch_nolock(
   int c
);
wint_t _ungetwch_nolock(
   wint_t c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak k posunutí.

## <a name="return-value"></a>Návratová hodnota

Obě funkce vrátí znak *c* v případě úspěšného ověření. Pokud dojde k chybě **_ungetch** vrací hodnotu **EOF** a **_ungetwch –** vrátí **WEOF**.

## <a name="remarks"></a>Poznámky

Tyto funkce vrátí znak *c* zpět do konzoly, což způsobí *c* bude další znak přečtený **_getch** nebo **_getche** (nebo **_getwch –** nebo **_getwche –**). **_ungetch** a **_ungetwch –** selhat, pokud jsou volány více než jednou před dalším čtením. *c* nemusí být argument **EOF** (nebo **WEOF**).

Verze s **_nolock** přípona jsou stejné s tím rozdílem, že nejsou chráněny před rušením jinými vlákny. Může být rychlejší, protože nejsou spojené režii uzamykáním ostatních vláken. Tyto funkce používejte pouze v kontextech bezpečných na vlákna, jako je například aplikace s jedním vláknem nebo pokud volající obor již zpracovává izolaci vláken.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettch**|**_ungetch**|**_ungetch**|**_ungetwch**|
|**_ungettch_nolock**|**_ungetch_nolock**|**_ungetch_nolock**|**_ungetwch_nolock**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ungetch**, **_ungetch_nolock –**|\<conio.h>|
|**_ungetwch**, **_ungetwch_nolock**|\<conio.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_ungetch.c
// compile with: /c
// In this program, a white-space delimited
// token is read from the keyboard. When the program
// encounters a delimiter, it uses _ungetch to replace
// the character in the keyboard buffer.
//

#include <conio.h>
#include <ctype.h>
#include <stdio.h>

int main( void )
{
   char buffer[100];
   int count = 0;
   int ch;

   ch = _getche();
   while( isspace( ch ) )      // Skip preceding white space.
      ch = _getche();
   while( count < 99 )         // Gather token.
   {
      if( isspace( ch ) )      // End of token.
         break;
      buffer[count++] = (char)ch;
      ch = _getche();
   }
   _ungetch( ch );            // Put back delimiter.
   buffer[count] = '\0';      // Null terminate the token.
   printf( "\ntoken = %s\n", buffer );
}
```

```Output

Whitetoken = White
```

## <a name="see-also"></a>Viz také:

[I/O konzoly a portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
