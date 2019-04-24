---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 03/25/2019
apiname:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: e2c237927aa133d33085be40b88789c1024d6b34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176197"
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Vyhledá další token v řetězci pomocí aktuálního národního prostředí nebo pomocí předaného národního prostředí. Tyto verze [strtok – _strtok_l –, wcstok –, _wcstok_l –, _mbstok –, _mbstok_l –](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s –** a **_mbstok_s_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Řetězec obsahující token nebo tokeny k vyhledání.

*oddělovače*<br/>
Sada oddělovacích znaků používat.

*context*<br/>
Používá k ukládání informací o poloze mezi voláními funkce.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na další token v parametru *str*. Vrátí **NULL** když nejsou nalezeny žádné další tokeny. Každé volání upraví parametr *str* nahrazením znaku null prvního oddělovače, ke které dojde po vráceném tokenu.

### <a name="error-conditions"></a>Chybové podmínky

|*str*|*oddělovače*|*context*|Návratová hodnota|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|Všechny|ukazatel na ukazatel s hodnotou null|**NULL**|**EINVAL**|
|Všechny|**NULL**|Všechny|**NULL**|**EINVAL**|
|Všechny|Všechny|**NULL**|**NULL**|**EINVAL**|

Pokud *str* je **NULL** ale *kontextu* je ukazatel na platný ukazatel kontextu, se nezobrazí žádná chyba.

## <a name="remarks"></a>Poznámky

**Strtok_s –** rodinu funkcí vyhledá další token v *str*. Sady znaků v *oddělovače* Určuje možné oddělovače tokenu, který má být vyhledána v *str* při aktuálním volání. **wcstok_s –** a **_mbstok_s –** jsou širokoznaké a vícebajtové verze **strtok_s –**. Argumenty a vrácené hodnoty **wcstok_s –** a **_wcstok_s_l –** jsou širokoznaké řetězce **_mbstok_s –** a **_mbstok_s_l –** jsou vícebajtové znakové řetězce. Tyto funkce chovají identicky jinak.

Tato funkce ověřuje své parametry. Když dojde k chybě, stejně jako v tabulce chybové podmínky vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **NULL**.

Při prvním volání **strtok_s –**, funkce Přeskočí úvodní oddělovače a vrátí ukazatel na první token v *str*, ukončí token znakem null. Další tokeny lze zjistit ze zbytku parametru *str* řadou volání **strtok_s –**. Každé volání **strtok_s –** upraví *str* vložením znaku null za token vrácený tímto voláním. *Kontextu* ukazatel uchovává informace o který řetězec se čte a kde v řetězci další token ke čtení. Přečíst další token z *str*, volání **strtok_s –** s **NULL** hodnota *str* argument a předejte stejný  *kontext* parametru. **NULL** *str* způsobí, že argument **strtok_s –** k vyhledání další token v upraveném *str*. *Oddělovače* argument přijímá jakoukoli hodnotu z jednoho volání na další tak, aby se sada oddělovačů může lišit.

Vzhledem k tomu, *kontextu* parametr nahrazuje statické vyrovnávací paměti používané **strtok –** a **_strtok_l –**, je možné analyzovat dva řetězce současně ve stejném vlákně.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí. Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md).

Verze těchto funkcí bez **_l** přípona použití národního prostředí aktuálního vlákna pro toto chování závislé na národním prostředí. Verze s **_l** přípona jsou stejné s tím rozdílem, že místo toho používají národní prostředí určené *národní prostředí* parametru. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<String.h > nebo \<wchar.h >|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|\_Kódování UNICODE & \_znakové sady MBCS nedefinovaná.|\_Znakové sady MBCS definovaný|_UNICODE definováno|
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

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
