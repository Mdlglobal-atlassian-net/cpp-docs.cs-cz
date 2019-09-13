---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 03/25/2019
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
ms.openlocfilehash: 1bbc5910e6242a0df262cc43b58815ea80ff9681
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946460"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Vyhledá další token v řetězci pomocí aktuálního národního prostředí nebo pomocí předaného národního prostředí. Tyto verze [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s** a **_mbstok_s_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězec obsahující token nebo tokeny, které se mají najít.

*oddělovače*<br/>
Sada oddělovačových znaků, které se mají použít.

*context*<br/>
Slouží k ukládání informací o poloze mezi voláními funkce.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na další token, který byl nalezen v *str*. Vrátí **hodnotu null** , pokud nejsou nalezeny žádné další tokeny. Každé volání upravuje *str* pomocí nahrazení znaku null pro první oddělovač, který nastane po vráceném tokenu.

### <a name="error-conditions"></a>Chybové stavy

|*str*|*oddělovače*|*context*|Návratová hodnota|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|Jakýmikoli|ukazatel na ukazatel s hodnotou null|**NULL**|**EINVAL**|
|Jakýmikoli|**NULL**|Jakýmikoli|**NULL**|**EINVAL**|
|Jakýmikoli|Jakýmikoli|**NULL**|**NULL**|**EINVAL**|

Pokud je str **null** , ale *kontext* je ukazatel na platný kontextový ukazatel, není k dispozici žádná chyba.

## <a name="remarks"></a>Poznámky

Rodina funkcí **strtok_s** vyhledá další token v *str*. Sada znaků v *oddělovačích* určuje možné oddělovače tokenu, který se má najít v *str* pro aktuální volání. **wcstok_s** a **_mbstok_s** jsou verze s velkým znakem a vícebajtovým znakem **strtok_s**. Argumenty a návratové hodnoty hodnot **wcstok_s** a **_wcstok_s_l** jsou řetězce s velkým počtem znaků; ty z **_mbstok_s** a **_mbstok_s_l** jsou vícebajtové znakové řetězce. Tyto funkce se chovají identicky jinak.

Tato funkce ověří své parametry. Pokud dojde k chybě, jako v tabulce chybové podmínky, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu null**.

Při prvním volání **strtok_s**funkce přeskočí úvodní oddělovače a vrátí ukazatel na první token v *str*a ukončí token pomocí znaku null. Další tokeny lze rozdělit z zbývající části *str* řadou volání na **strtok_s**. Každé volání **strtok_s** upravuje *str* vložením znaku null za token vrácený tímto voláním. *Kontextový* ukazatel uchovává přehled o tom, který řetězec je čten a kde v řetězci je třeba číst další token. Chcete-li číst další token z *str*, zavolejte **Strtok_s** s hodnotou **null** pro argument *str* a předejte stejný *kontextový* parametr. Argument **null** *str* způsobí, že **strtok_s** vyhledá další token v upraveném *str*. Argument *oddělovače* může mít libovolnou hodnotu z jednoho volání na další, aby se sada oddělovačů mohla lišit.

Vzhledem k tomu, že parametr *Context* nahrazuje statické vyrovnávací paměti používané v **strtok** a **_strtok_l**, je možné rozložit dva řetězce současně ve stejném vlákně.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí. Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md).

Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí vlákna pro toto chování závislé na národním prostředí. Verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají národní prostředí určené parametrem *národního prostředí* . Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtok_s**|\<String. h >|
|**_strtok_s_l**|\<String. h >|
|**wcstok_s**,<br />**_wcstok_s_l**|\<String. h > nebo \<WCHAR. h >|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|\_Kódování Unicode \_& znakové sady MBCS není definováno.|\_Definice znakové sady MBCS|_UNICODE definováno|
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

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
