---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 4/2/2020
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
- _o__mbstok
- _o__mbstok_l
- _o_strtok
- _o_wcstok
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: d228d9824c534a21e4a22797e4b070e6d8d0b179
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365200"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Najde další token v řetězci pomocí aktuální národní prostředí nebo zadané národní prostředí, které je předáno. K dispozici jsou bezpečnější verze těchto funkcí. viz [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok** a **_mbstok_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strToken*<br/>
Řetězec obsahující token nebo tokeny.

*strDelimit*<br/>
Sada oddělovacích znaků.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na další token nalezený v *strToken*. Funkce vrátí **hodnotu NULL,** pokud nejsou nalezeny žádné další tokeny. Každé volání upraví *strToken* nahrazením nulového znaku pro první oddělovač, ke kterému dojde po vrácený token.

## <a name="remarks"></a>Poznámky

Funkce **strtok** najde další token v *strToken*. Sada znaků v *strDelimit* určuje možné oddělovače tokenu, který se nachází v *strToken* na aktuální volání. **wcstok** a **_mbstok** jsou širokoúhlé a vícebajtové verze **strtoku**. Argumenty a vrácená hodnota **wcstok** jsou řetězce širokých znaků; **_mbstok** jsou řetězce vícebajtových znaků. Tyto tři funkce se chovají stejně jinak.

> [!IMPORTANT]
> Tyto funkce vznikají potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti jsou častou metodou systémového útoku, což vede k neoprávněnému zvýšení oprávnění. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Při prvním volání **strtok**funkce přeskočí přední oddělovače a vrátí ukazatel na první token v *strToken*, ukončení tokenu s nulovým znakem. Další tokeny mohou být rozděleny ze zbytku *strToken* řadou volání **strtok**. Každé volání **strtok** upraví *strToken* vložením nulového znaku za **token** vrácený tímto voláním. Chcete-li číst další token z *strToken*, volejte **strtok** s hodnotou **NULL** pro argument *strToken.* **Null** *strToken* argument způsobí **strtok** hledat další token v modifikované *strToken*. Argument *strDelimit* může trvat libovolnou hodnotu z jednoho volání na další tak, aby sada oddělovačů se může lišit.

Výstupní hodnota je ovlivněna nastavením nastavení **kategorie LC_CTYPE** národního prostředí. Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md).

Verze těchto funkcí bez **přípony _l** pro toto chování závislé na národním prostředí používají aktuální národní prostředí. Verze s **příponou _l** jsou identické s tím rozdílem, že místo toho používají parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> Každá funkce používá místní statické proměnné pro analýzu řetězce na tokeny. Proto více vláken může současně volat tyto funkce bez nežádoucích účinků. Však v rámci jednoho vlákna prokládání volání jedné z těchto funkcí je vysoce pravděpodobné, že k poškození dat a nepřesné výsledky. Při analýzách různých řetězců dokončete analýzu jednoho řetězce před zahájením analýzy dalšího. Také uvědomte si potenciál pro nebezpečí při volání jedné z těchto funkcí z smyčky, kde je volána jiná funkce. Pokud druhá funkce skončí pomocí jedné z těchto funkcí, dojde k prokládání posloupnosti volání, což spustí poškození dat.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> \<nebo wchar.h>|
|**_mbstok**, **_mbstok_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
