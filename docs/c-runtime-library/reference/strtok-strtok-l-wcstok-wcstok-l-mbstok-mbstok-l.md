---
title: strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
ms.date: 03/25/2019
api_name:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
ms.openlocfilehash: 62ed9edc6ec5a7ee60223f1c5e908aa14f421a25
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957643"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l

Vyhledá další token v řetězci pomocí aktuálního národního prostředí nebo zadaného národního prostředí, které je předáno. K dispozici jsou bezpečnější verze těchto funkcí; viz [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).

> [!IMPORTANT]
> **_mbstok** a **_mbstok_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na další token, který najdete v *strToken*. Pokud žádné další tokeny nenaleznou, funkce vrátí **hodnotu null** . Každé volání upravuje *strToken* nahrazením znaku null pro první oddělovač, který nastane po vráceném tokenu.

## <a name="remarks"></a>Poznámky

Funkce **strtok** vyhledá další token v *strToken*. Sada znaků v *strDelimit* určuje možné oddělovače tokenu, který se má najít v *strToken* pro aktuální volání. **wcstok** a **_mbstok** jsou verze s velkým znakem a vícebajtovým znakem **strtok**. Argumenty a návratová hodnota **wcstok** jsou řetězce s velkým počtem znaků; ty z **_mbstok** jsou vícebajtové znakové řetězce. Tyto tři funkce se chovají identicky jinak.

> [!IMPORTANT]
> Tyto funkce se dotýkají potenciální hrozby týkající se problému s přetečením vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti představují častější způsob útoku na systém, což vede k neoprávněnému zvýšení oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Při prvním volání **strtok**funkce přeskočí úvodní oddělovače a vrátí ukazatel na první token v *strToken*a ukončí token znakem null. Další tokeny lze rozdělit mimo zbytek *strToken* řadou volání **strtok**. Každé volání **strtok** upraví *strToken* vložením znaku null za **token** vrácený tímto voláním. Pro čtení dalšího tokenu z *strToken*volejte **strtok** s hodnotou **null** pro argument *strToken* . Argument **null** *strToken* způsobí, že **strtok** ve změněném *strToken*vyhledá další token. Argument *strDelimit* může přijmout libovolnou hodnotu z jednoho volání na další, aby se sada oddělovačů mohla lišit.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí. Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md).

Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí. Verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

> [!NOTE]
> Každá funkce používá pro analýzu řetězce na tokeny statickou proměnnou místního vlákna. Proto může více vláken současně volat tyto funkce bez nežádoucích účinků. V rámci jednoho vlákna ale vzájemná volání jedné z těchto funkcí je vysoce pravděpodobná, což způsobí poškození dat a nepřesné výsledky. Při analýze různých řetězců dokončete analýzu jednoho řetězce předtím, než začnete analyzovat další. Také je třeba si uvědomit, že nebezpečí při volání jedné z těchto funkcí ze smyčky, kde je volána jiná funkce, je také možné znát. Pokud druhá funkce ukončí použití některé z těchto funkcí, výsledkem provedená posloupnost volání bude mít za následek vynechání poškození dat.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtok**|\<String. h >|
|**wcstok**|\<String. h > nebo \<WCHAR. h >|
|**_mbstok**, **_mbstok_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
