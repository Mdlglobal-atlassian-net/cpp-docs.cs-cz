---
title: ungetc, ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 484af7b72f860a8a9d12cf0b62444871caad4675
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361300"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Odešle znak zpět do datového proudu.

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

*C*<br/>
Znak, který má být tlačen.

*Proudu*<br/>
Ukazatel na **strukturu FILE.**

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, každá z těchto funkcí vrátí argument znaku *c*. Pokud *c* nelze posunout zpět nebo pokud nebyl přečten žádný znak, vstupní datový proud se nezmění a **ungetc** vrátí **EOF**; **ungetwc** vrátí **WEOF**. Pokud je *datový proud* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Je-li spuštění povoleno pokračovat, **EOF** nebo **WEOF** je vrácena a **errno** je nastavena na **EINVAL**.

Informace o těchto a dalších kódech chyb naleznete [v tématu _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **ungetc** posune znak *c* zpět do *datového proudu* a vymaže indikátor konce souboru. Datový proud musí být otevřen pro čtení. Následná operace čtení *v datovém proudu* začíná *písmenem c*. Pokus o push **EOF** na datový proud pomocí **ungetc** je ignorována.

Znaky umístěné na datovém proudu **ungetc** může být vymazány, pokud **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**, nebo [převinout zpět](rewind.md) je volána před znak je číst z datového proudu. Indikátor pozice souboru bude mít hodnotu, kterou měl před odsunutím znaků. Externí úložiště odpovídající datovému proudu se nezmění. Na úspěšné **ungetc** volání proti textového proudu indikátor pozice souboru není určen, dokud všechny pushed-back znaky jsou čteny nebo zahozeny. Při každém úspěšném volání **ungetc** proti binárnímu datovému proudu je indikátor pozice souboru snížen; Pokud jeho hodnota byla 0 před voláním, hodnota není definována po volání.

Výsledky jsou nepředvídatelné, pokud **ungetc** je volána dvakrát bez operace čtení nebo umístění souboru mezi dvěma voláními. Po volání **fscanf**může volání **ungetc** selhat, pokud nebyla provedena jiná operace čtení (například **getc).** Je to **proto, že fscanf** sám volá **ungetc**.

**ungetwc** je širokoznaková verze **ungetc**. Však na každé úspěšné **ungetwc** volání proti text nebo binární datový proud, hodnota indikátoru pozice souboru není určen, dokud všechny pushed-back znaky jsou čteny nebo zahozeny.

Tyto funkce jsou bezpečné pro přístup z více vláken a zamknout citlivá data během provádění. O verzi bez zamykání viz [_ungetc_nolock _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> \<nebo wchar.h>|

Konzola není podporována v aplikacích univerzální platformy Windows (UPW). Standardní popisovače datového proudu, které jsou přidruženy ke **konzole, stdin**, **stdout**a **stderr**, musí být přesměrovány před c run-time funkce je možné použít v aplikacích UPW. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[I/O proudu](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
