---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 03/25/2019
apiname:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 22dd01a0b2558c83ca1e25875a2ace7dd4ee15c0
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476913"
---
# <a name="strtok-strtokl-wcstok-wcstokl-mbstok-mbstokl"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Vyhledá další token v řetězci pomocí aktuálního národního prostředí nebo zadaného národního prostředí, které je předáno. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [strtok_s – _strtok_s_l –, wcstok_s –, _wcstok_s_l –, _mbstok_s –, _mbstok_s_l –](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok –** a **_mbstok_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na další token v parametru *tokenu %{strtoken/*. Funkce vrací **NULL** když nejsou nalezeny žádné další tokeny. Každé volání upraví parametr *tokenu %{strtoken/* nahrazením znaku null prvního oddělovače, ke které dojde po vráceném tokenu.

## <a name="remarks"></a>Poznámky

**Strtok –** funkce vyhledá další token v *tokenu %{strtoken/*. Sady znaků v *strDelimit* Určuje možné oddělovače tokenu, který má být vyhledána v *tokenu %{strtoken/* při aktuálním volání. **wcstok –** a **_mbstok –** jsou širokoznaké a vícebajtové verze **strtok –**. Argumenty a vrácené hodnoty **wcstok –** jsou širokoznaké řetězce **_mbstok –** jsou vícebajtové znakové řetězce. Tyto tři funkce chovají identicky jinak.

> [!IMPORTANT]
> Tyto funkce se vám účtovat potenciální ohrožení způsobené problémem přetečení vyrovnávací paměti. Problémů přetečení vyrovnávací paměti jsou častou metodou útoku na systém. Výsledkem je negarantované zvýšení úrovně oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

Při prvním volání **strtok –**, funkce Přeskočí úvodní oddělovače a vrátí ukazatel na první token v *tokenu %{strtoken/*, ukončí token znakem null. Další tokeny lze zjistit ze zbytku parametru *tokenu %{strtoken/* řadou volání **strtok –**. Každé volání **strtok –** upraví *tokenu %{strtoken/* vložením znaku null za **token** vrácený tímto voláním. Přečíst další token z *tokenu %{strtoken/*, volání **strtok –** s **NULL** hodnota *tokenu %{strtoken/* argument. **NULL** *tokenu %{strtoken/* způsobí, že argument **strtok –** k vyhledání další token v upraveném *tokenu %{strtoken/*. *StrDelimit* argument přijímá jakoukoli hodnotu z jednoho volání na další tak, aby se sada oddělovačů může lišit.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí. Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md).

Verze těchto funkcí bez **_l** přípona používají aktuální národní prostředí pro toto chování závislé na národním prostředí. Verze s **_l** přípona jsou stejné s tím rozdílem, že používají Předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

> [!NOTE]
> Každá funkce používá statická proměnná místního vlákna k analýze řetězec do tokenů. Proto více vláken může současně volání těchto funkcí bez nežádoucí účinky. Nicméně v jednom vlákně, prokládání volání jedné z těchto funkcí je velmi pravděpodobné vytvářejí poškození dat a jejich výsledky. Při analýze různých řetězců, dokončete parsování jeden řetězec před zahájením k další analýze. Navíc být vědomi potenciální nebezpečí při volání jedné z těchto funkcí z v rámci smyčky, kde je volán jiné funkci. Pokud jiná funkce končí pomocí jedné z těchto funkcí, budou výsledkem prokládané posloupnost volání, aktivuje poškození dat.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<String.h > nebo \<wchar.h >|
|**_mbstok**, **_mbstok_l**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
