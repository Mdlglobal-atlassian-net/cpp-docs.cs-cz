---
title: setlocale, _wsetlocale
ms.date: 11/04/2016
apiname:
- _wsetlocale
- setlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
ms.openlocfilehash: 0f2c0478ba5898ab369a04362734891f6d45cf42
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548535"
---
# <a name="setlocale-wsetlocale"></a>setlocale, _wsetlocale

Nastaví nebo načte národní prostředí runtime.

## <a name="syntax"></a>Syntaxe

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parametry

*Kategorie*<br/>
Kategorie ovlivněná národním prostředím

*Národní prostředí*<br/>
Specifikátor národního prostředí

## <a name="return-value"></a>Návratová hodnota

Pokud platné *národní prostředí* a *kategorie* jsou uvedeny, vrací ukazatel na řetězec přidružený k zadanému *národní prostředí* a *kategorie*. Pokud *národní prostředí* nebo *kategorie* není platný, vrátí ukazatel s hodnotou null a aktuální nastavení národního prostředí programu se nezmění.

Například volání

```C
setlocale( LC_ALL, "en-US" );
```

nastaví všechny kategorie, aby vracely pouze řetězec

```Output
en-US
```

Můžete zkopírovat řetězec vrácený funkcí **setlocale** obnovit tuto část informací o národním prostředí programu. Globální nebo vlákno místní úložiště se používá pro řetězec vrácený funkcí **setlocale**. Pozdější volání **setlocale** řetězec přepíšou, což způsobí neplatnost ukazatelů na řetězec vrácených dřívějšími voláními.

## <a name="remarks"></a>Poznámky

Použití **setlocale** funkce nastavení, změnit nebo dotazy aktuální národní prostředí informace o programu určené *národní prostředí* a *kategorie*. *národní prostředí* odkazuje na místo (země/oblast a jazyk), pro které můžete přizpůsobit některé aspekty programu. Ke kategoriím závislým na národním prostředí patří formátování dat nebo zobrazovací formát pro peněžní hodnoty. Pokud nastavíte *národní prostředí* na výchozí řetězec jazyka, který se podporuje ve vašem počítači více forem, měli byste zkontrolovat **setlocale** návratová hodnota jazyk, který je v platnosti. Například pokud nastavíte *národní prostředí* na "čínština" návratová hodnota může být buď "čínština (zjednodušená)" nebo "čínština (tradiční)".

**_wsetlocale** je verze širokého znaku **setlocale**; *národní prostředí* argument a návratová hodnota funkce **_wsetlocale** jsou širokoznaké řetězce. **_wsetlocale** a **setlocale** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale –**|**setlocale**|**setlocale**|**_wsetlocale**|

*Kategorie* argument určuje části informací o národním prostředí programu, které tím ovlivníte. Makra použitá pro argument *kategorie* a části programu, které ovlivňují, jsou následující:

|*kategorie* příznak|Ovlivňuje|
|-|-|
**LC_ALL**|Všechny kategorie, jak je uvedeno níže.
**LC_COLLATE**|**Strcoll –**, **_stricoll –**, **wcscoll –**, **_wcsicoll –**, **strxfrm –**, **_ strncoll –**, **_strnicoll –**, **_wcsncoll –**, **_wcsnicoll –**, a **wcsxfrm –** funkce.
**LC_CTYPE**|Funkce zpracování znaků (s výjimkou **isdigit**, **isxdigit**, **mbstowcs**, a **mbtowc**, které nejsou ovlivněny).
**LC_MONETARY**|Informace o formátování měny vrácené **localeconv** funkce.
**LC_NUMERIC**|Znak pro rutiny formátovaného výstupu desetinné čárky (například **printf**), pro rutiny převodu dat a informace nefinančního formátování vrácené **localeconv**. Kromě znaku desetinné čárky **LC_NUMERIC** nastaví oddělovač tisíců a seskupení vrácený řetězec řídící [localeconv](localeconv.md).
**LC_TIME**|**Strftime** a **wcsftime** funkce.

Tato funkce ověřuje parametr kategorie. Pokud parametr kategorie není jedna z hodnot uvedených v předchozí tabulce, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce nastaví **errno** k **EINVAL** a vrátí **NULL**.

*Národní prostředí* argument je ukazatel na řetězec, který určuje národní prostředí. Informace o formátu *národní prostředí* argument, naleznete v tématu [názvy národních prostředí, jazyků a Country/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Pokud *národní prostředí* odkazuje na prázdný řetězec, národní prostředí, které je definováno implementací nativního prostředí. Hodnota **C** Určuje minimální prostředí vyhovující standardu ANSI pro překlad. **C** národní prostředí předpokládá, že všechny **char** datové typy mají 1 bajt a jejich hodnota je vždy menší než 256.

Při spuštění programu se spustí ekvivalent následujícího příkazu:

`setlocale( LC_ALL, "C" );`

*Národní prostředí* argument přijímá název národního prostředí, řetězec jazyka, řetězec jazyka a země nebo oblasti, znakovou stránku nebo řetězec jazyka, kód země/oblasti a znakovou stránku. Sada dostupných názvů národního prostředí, jazyků, kódů země/oblasti a znakových stránek obsahuje všechny prvky, které jsou podporovány v rozhraní API Windows NLS, kromě znakových stránek, které vyžadují více než dva bajty na znak, například UTF-7 a UTF-8. Pokud zadáte hodnotu znakové stránky UTF-7 nebo UTF-8, **setlocale** selže a vrátí **NULL**. Sada názvů národních prostředí podporovaných **setlocale** jsou popsány v [názvy národních prostředí, jazyků a Country/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Sada řetězců jazyka a země/oblast nepodporuje **setlocale** jsou uvedeny v [Language Strings](../../c-runtime-library/language-strings.md) a [Country/Region Strings](../../c-runtime-library/country-region-strings.md). Doporučujeme, abyste s ohledem na výkon a údržbu řetězců národního prostředí formu národního prostředí integrovali do kódu nebo serializovali do úložiště. U řetězců názvu národního prostředí je méně pravděpodobné, že aktualizací operačního systému dojde k jejich změně, než v případě formy pro název jazyka a země či oblasti.

Ukazatel s hodnotou null, který je předán jako *národní prostředí* argument určuje **setlocale** dotaz namísto nastavení mezinárodního prostředí. Pokud *národní prostředí* argument je ukazatel s hodnotou null, aktuální nastavení národního prostředí programu se nezmění. Místo toho **setlocale** vrací ukazatel na řetězec, který je přidružen *kategorie* národního prostředí aktuálního vlákna. Pokud *kategorie* argument je **LC_ALL**, vrátí funkce řetězec označující aktuální nastavení všech kategorií, oddělené středníky. Například sekvence volání

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

vrací

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

což je řetězec, který je přidružen **LC_ALL** kategorie.

Následující příklady se týkají **LC_ALL** kategorie. Každý z řetězců .OCP a .AKT lze použít místo čísla znakové stránky a určit tak výchozí znakovou stránku OEM nebo případně výchozí znakovou stránku ANSI pro uživatele.

- `setlocale( LC_ALL, "" );`

   Nastaví národní prostředí na výchozí hodnotu, což je výchozí znaková stránka ANSI pro uživatele získaná z operačního systému.

- `setlocale( LC_ALL, ".OCP" );`

   Explicitně nastaví národní prostředí na aktuální znakovou stránku OEM získanou z operačního systému.

- `setlocale( LC_ALL, ".ACP" );`

   Nastaví národní prostředí na znakovou stránku ANSI získanou z operačního systému.

- `setlocale( LC_ALL, "<localename>" );`

   Nastaví národní prostředí na název národního prostředí, který je označen  *\<localename >*.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Nastaví národní prostředí na jazyk a zemi/oblast uvedené v  *\<jazyk >* a  *\<země >* společně s výchozí znakové stránky získané z hostitele operační systém.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Nastaví národní prostředí pro jazyk, země/oblast a znakovou stránku indikován  *\<jazyk >*,  *\<země >*, a  *\<code_page >* řetězce. Můžete použít různé kombinace jazyka, země/oblasti a znakové stránky. Například toto volání nastaví národní prostředí na hodnotu francouzština, Kanada se znakovou stránkou 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Toto volání nastaví národní prostředí na hodnotu francouzština, Kanada s výchozí znakovou stránkou ANSI:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Toto volání nastaví národní prostředí na hodnotu francouzština, Kanada s výchozí znakovou stránkou OEM:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Nastaví národní prostředí na jazyk, ve kterém je indikován  *\<jazyk >* a použije výchozí zemi/oblast pro zadaný jazyk a výchozí ANSI znakovou stránku pro zemi/oblast získanou z hostitele operační systém. Například následující volání **setlocale** jsou funkčně ekvivalentní:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   S ohledem na výkon a údržbu doporučujeme použít první z uvedených forem.

- `setlocale( LC_ALL, ".<code_page>" );`

   Nastaví znakovou stránku na hodnotu *< code_page >*, společně s výchozí země/oblast a jazyk (podle definice v hostitelském operačním systému) pro zadanou znakovou stránku.

Kategorie musí být buď **LC_ALL** nebo **LC_CTYPE** Změna znakové stránky. Například, pokud výchozí země/oblast a jazyk hostitelského operačního systému "USA" a "Angličtina", následující dvě volání **setlocale** jsou funkčně ekvivalentní:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Další informace najdete v tématu [setlocale](../../preprocessor/setlocale.md) – Direktiva pragma v [C/C++ Preprocessor Reference](../../preprocessor/c-cpp-preprocessor-reference.md).

Funkce [_configthreadlocale](configthreadlocale.md) je slouží ke kontrole, jestli **setlocale** ovlivňuje národní prostředí všech vláken v programu nebo pouze národní prostředí volajícího vlákna.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setlocale**|\<Locale.h >|
|**_wsetlocale**|\<Locale.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_setlocale.c
//
// This program demonstrates the use of setlocale when
// using two independent threads.
//

#include <locale.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date in the current
// locale's format.
int get_date(unsigned char* str)
{
    __time64_t ltime;
    struct tm  thetime;

    // Retrieve the current time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // "%#x" is the long date representation in the
    // current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm *)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to the argument
// and prints the date.
uintptr_t __stdcall SecondThreadFunc( void* pArguments )
{
    unsigned char str[BUFF_SIZE];
    char * locale = (char *)pArguments;

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, locale));

    // Retrieve the date string from the helper function
    if (get_date(str) == 0)
    {
        printf("The date in %s locale is: '%s'\n", locale, str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread sets the locale to English
// and then spawns a second thread (above) and prints the date.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Configure per-thread locale to cause all subsequently created
    // threads to have their own locale.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the locale of the main thread to US English.
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "en-US"));

    // Create the second thread with a German locale.
    // Our thread function takes an argument of the locale to use.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      "de-DE", 0, &threadID );

    if (get_date(str) == 0)
    {
        // Retrieve the date string from the helper function
        printf("The date in en-US locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Viz také:

[Názvy národních prostředí, jazyků a Country/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
