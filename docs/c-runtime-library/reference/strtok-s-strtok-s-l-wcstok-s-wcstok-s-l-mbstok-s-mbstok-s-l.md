---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: 9fe89fb897a5459b16c49060359b4bb40bc062a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365224"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Vyhledá další token v řetězci pomocí aktuálního národního prostředí nebo pomocí předaného národního prostředí. Tyto verze [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s** a **_mbstok_s_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec obsahující token nebo tokeny najít.

*Oddělovače*<br/>
Sada znaků oddělovače, které chcete použít.

*Kontextu*<br/>
Slouží k ukládání informací o poloze mezi voláními funkce.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na další token nalezený v *str*. Vrátí **hodnotu NULL,** pokud nejsou nalezeny žádné další tokeny. Každé volání upraví *str* nahrazením znaku null pro první oddělovač, ke kterému dochází po vrácený token.

### <a name="error-conditions"></a>Chybové stavy

|*Str*|*Oddělovače*|*Kontextu*|Návratová hodnota|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**Null**|jakékoli|ukazatel na ukazatel s hodnotou null|**Null**|**EINVAL**|
|jakékoli|**Null**|jakékoli|**Null**|**EINVAL**|
|jakékoli|jakékoli|**Null**|**Null**|**EINVAL**|

Pokud *str* je **NULL,** ale *kontext* je ukazatel na platný ukazatel kontextu, neexistuje žádná chyba.

## <a name="remarks"></a>Poznámky

**Strtok_s** rodina funkcí najde další token v *str*. Sada znaků v *oddělovači* určuje možné oddělovače tokenu, který se nachází v *str* na aktuální volání. **wcstok_s** a **_mbstok_s** jsou verze **strtok_s**s širokými znaky a vícebajtovými znaky . Argumenty a vrácené hodnoty **wcstok_s** a **_wcstok_s_l** jsou řetězce s širokými znaky; **_mbstok_s** a **_mbstok_s_l** jsou řetězce vícebajtových znaků. Tyto funkce se chovají stejně jinak.

Tato funkce ověřuje její parametry. Pokud dojde k chybovému stavu, jako v tabulce Chybové podmínky, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** **eINVAL** a vrátit **NULL**.

Při prvním volání **strtok_s**funkce přeskočí úvodní oddělovače a vrátí ukazatel na první token v *str*a ukončí token s nulovým znakem. Další tokeny mohou být rozděleny ze zbytku *str* řadou volání **strtok_s**. Každé volání **strtok_s** upravuje *str* vložením nulového znaku za token vrácený tímto voláním. Ukazatel *kontextu* sleduje, který řetězec se čte a kde v řetězci má být přečten další token. Chcete-li číst další token z *str*, volání **strtok_s** s hodnotou **NULL** pro argument *str* a předat stejný parametr *kontextu.* Argument **NULL** *str* **způsobí, že strtok_s** hledat další token v modifikovanéstr . *str* *Oddělovače* argument může trvat libovolnou hodnotu z jednoho volání na další tak, aby sada oddělovačů se může lišit.

Vzhledem k tomu, že parametr *kontextu* nahrazuje statické vyrovnávací paměti používané v **strtok** a **_strtok_l**, je možné analyzovat dva řetězce současně ve stejném vlákně.

Výstupní hodnota je ovlivněna nastavením nastavení **kategorie LC_CTYPE** národního prostředí. Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md).

Verze těchto funkcí bez **přípony _l** pro toto chování závislé na národním prostředí používají aktuální národní prostředí vlákna. Verze s **příponou _l** jsou identické s tím rozdílem, že místo toho používají národní prostředí určené parametrem *národního prostředí.* Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> \<nebo wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|\_Nedefinována \_& mbcs UNICODE|\_MBCS definice|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>Příklad

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
