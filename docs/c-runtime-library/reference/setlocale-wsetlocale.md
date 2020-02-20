---
title: setlocale, _wsetlocale
description: Popisuje funkce knihovny modulu runtime jazyka Microsoft (CRT) setlocale a _wsetlocale.
ms.date: 01/28/2020
api_name:
- _wsetlocale
- setlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: b1c7b739e671caebc51022945a369a632ecebb9e
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473863"
---
# <a name="setlocale-_wsetlocale"></a>setlocale, _wsetlocale

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

\ *kategorie*
Kategorie ovlivněná národním prostředím

\ *národního prostředí*
Specifikátor národního prostředí

## <a name="return-value"></a>Návratová hodnota

Pokud je zadáno platné *národní prostředí* a *kategorie* , vrátí ukazatel na řetězec přidružený k zadanému *národnímu prostředí* a *kategorii*. Pokud *národní prostředí* nebo *kategorie* nejsou platné, vrátí ukazatel s hodnotou null a aktuální nastavení národního prostředí programu se nezmění.

Například volání

```C
setlocale( LC_ALL, "en-US" );
```

nastaví všechny kategorie, aby vracely pouze řetězec

```Output
en-US
```

Můžete zkopírovat řetězec vrácený funkcí **setlocale** pro obnovení této části informací o národním prostředí programu. Pro řetězec vrácený funkcí **setlocale**se používá globální úložiště nebo Thread Local. Později volání funkce **setlocale** přepíše řetězec, který zruší platnost ukazatelů na řetězec vrácený předchozími voláními.

## <a name="remarks"></a>Poznámky

Funkci **setlocale** použijte k nastavení, změně nebo dotazování některých nebo všech informací o národním prostředí aktuálního programu určených *národním prostředím* a *kategorií*. *národní prostředí* odkazuje na místní (země/oblast a jazyk), pro které můžete přizpůsobit některé aspekty programu. Ke kategoriím závislým na národním prostředí patří formátování dat nebo zobrazovací formát pro peněžní hodnoty. Pokud nastavíte *národní prostředí* na výchozí řetězec pro jazyk, který má v počítači více podporovaných formulářů, měli byste zjistit, který jazyk je platný, v případě, že použijete návratový parametr **setlocale** . Pokud jste například nastavili *locale* na "čínština", vrácená hodnota může být buď "Čínština-zjednodušená", nebo "tradiční čínština".

**_wsetlocale** je verze s libovolným znakem **.** Argument *locale* a návratová hodnota **_wsetlocale** jsou řetězce s velkým počtem znaků. **_wsetlocale** a **setlocale** se chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

Argument *Category* určuje části informací o národním prostředí programu, které jsou ovlivněny. Makra použitá pro *kategorii* a části programu, které ovlivňují, jsou následující:

|příznak *kategorie*|Ovlivňuje|
|-|-|
| **LC_ALL** | Všechny kategorie, jak je uvedeno níže. |
| **LC_COLLATE** | Funkce **strcoll –** , **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**a **Wcsxfrm** . |
| **LC_CTYPE** | Funkce pro zpracování znaků (s výjimkou **číslic**, **isxdigit**, **mbstowcs**a **mbtowc**, které nejsou ovlivněny). |
| **LC_MONETARY** | Informace o formátování měny vrácené funkcí **localeconv** . |
| **LC_NUMERIC** | Znak desetinné čárky pro naformátované výstupní rutiny (například **printf**) pro rutiny převodu dat a pro nepeněžní informace o formátování vrácené funkcí **localeconv**. Kromě znaku desetinné čárky **LC_NUMERIC** nastaví oddělovač tisíců a řetězec ovládacího prvku seskupení vrácený funkcí [localeconv](localeconv.md). |
| **LC_TIME** | Funkce **strftime** a **wcsftime** . |

Tato funkce ověřuje parametr kategorie. Pokud parametr Category není jedna z hodnot uvedených v předchozí tabulce, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí **hodnotu null**.

Argument *locale* je ukazatel na řetězec, který určuje národní prostředí. Informace o formátu argumentu *národního prostředí* najdete v tématu [názvy národních prostředí, jazyky a řetězce země/oblasti](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Pokud *národní prostředí* odkazuje na prázdný řetězec, národní prostředí je nativní prostředí definované implementací. Hodnota **C** určuje minimální prostředí vyhovující standardu ANSI pro překlad C. Národní prostředí **jazyka C** předpokládá, že všechny datové typy **char** mají 1 bajt a jejich hodnota je vždy menší než 256.

Při spuštění programu se spustí ekvivalent následujícího příkazu:

`setlocale( LC_ALL, "C" );`

Argument *locale* může mít název národního prostředí, řetězec jazyka, řetězec jazyka a kód země nebo oblasti, znakovou stránku nebo řetězec jazyka, kód země/oblasti a znakovou stránku. Sada dostupných názvů národního prostředí, jazyků, kódů zemí a oblastí a znakových stránek obsahuje všechny, které jsou podporovány rozhraním API Windows NLS. Sada názvů národních prostředí podporovaných pomocí funkce **setlocale** je popsána v tématu [názvy národních prostředí, jazyky a řetězce země/oblasti](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Sada řetězců jazyka a země/oblasti, kterou podporuje **setlocale** , je uvedena v části [jazykové řetězce](../../c-runtime-library/language-strings.md) a [řetězce země/oblasti](../../c-runtime-library/country-region-strings.md). Doporučujeme, abyste s ohledem na výkon a údržbu řetězců národního prostředí formu národního prostředí integrovali do kódu nebo serializovali do úložiště. U řetězců názvu národního prostředí je méně pravděpodobné, že aktualizací operačního systému dojde k jejich změně, než v případě formy pro název jazyka a země či oblasti.

Ukazatel s hodnotou null, který je předán jako argument *národního prostředí* , říká příkazu **setlocale** na dotaz namísto na nastavení mezinárodního prostředí. Pokud argument *locale* je ukazatel s hodnotou null, aktuální nastavení národního prostředí programu se nezmění. Místo toho příkaz **setlocale** vrátí ukazatel na řetězec, který je přidružený ke *kategorii* aktuálního národního prostředí vlákna. Pokud je argument *kategorie* **LC_ALL**, funkce vrátí řetězec, který označuje aktuální nastavení každé kategorie, oddělené středníky. Například sekvence volání

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

což je řetězec, který je spojen s kategorií **LC_ALL** .

Následující příklady se týkají kategorie **LC_ALL** . Oba řetězce ". OCP "a". K určení použití znakové stránky OEM default a uživatele výchozí znakové stránky ANSI pro daný název národního prostředí (v uvedeném pořadí) se dá použít AKT (AKT) místo čísla kódové stránky.

- `setlocale( LC_ALL, "" );`

   Nastaví národní prostředí na výchozí hodnotu, což je výchozí znaková stránka ANSI pro uživatele získaná z operačního systému. Název národního prostředí je nastaven na hodnotu vrácenou funkcí [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Znaková stránka je nastavena na hodnotu vrácenou funkcí [GetACP](/windows/win32/api/winnls/nf-winnls-getacp).

- `setlocale( LC_ALL, ".OCP" );`

   Nastaví národní prostředí na aktuální znakovou stránku OEM získanou z operačního systému. Název národního prostředí je nastaven na hodnotu vrácenou funkcí [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Znaková stránka je nastavena na hodnotu [LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) pro výchozí název národního prostředí pro uživatele pomocí [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, ".ACP" );`

   Nastaví národní prostředí na znakovou stránku ANSI získanou z operačního systému. Název národního prostředí je nastaven na hodnotu vrácenou funkcí [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Znaková stránka je nastavena na hodnotu [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pro výchozí název národního prostředí pro uživatele pomocí [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<localename>" );`

   Nastaví národní prostředí na název národního prostředí, který je určen *\<locale >* . Znaková stránka je nastavena na hodnotu [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pro zadaný název národního prostředí [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>" );`

   Nastaví národní prostředí na jazyk a zemi/oblast, které uvádí *\<language >* a *\<země >* , spolu s výchozí znakovou stránkou získanou z hostitelského operačního systému. Znaková stránka je nastavena na hodnotu [LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) pro zadaný název národního prostředí [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Nastaví národní prostředí na jazyk, zemi nebo oblast a znakovou stránku určenou *>\<jazyka*, *\<země >* a *\<* code_page > řetězců. Můžete použít různé kombinace jazyka, země/oblasti a znakové stránky. Například toto volání nastaví národní prostředí na hodnotu francouzština, Kanada se znakovou stránkou 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Toto volání nastaví národní prostředí na hodnotu francouzština, Kanada s výchozí znakovou stránkou ANSI:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Toto volání nastaví národní prostředí na hodnotu francouzština, Kanada s výchozí znakovou stránkou OEM:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Nastaví národní prostředí na jazyk, který je určen *\<m jazykovým >* a používá výchozí zemi nebo oblast pro zadaný jazyk a výchozí znakovou stránku ANSI pro danou zemi nebo oblast získanou z hostitelského operačního systému. Například následující volání funkce **setlocale** jsou funkčně ekvivalentní:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   S ohledem na výkon a údržbu doporučujeme použít první z uvedených forem.

- `setlocale( LC_ALL, ".<code_page>" );`

   Nastaví znakovou stránku na hodnotu určenou v *< code_page >* spolu s výchozí zemí/oblastí a jazykem (jak je definováno hostitelským operačním systémem) pro zadanou znakovou stránku.

Aby bylo možné změnit znakovou stránku, musí být kategorie buď **LC_ALL** , nebo **LC_CTYPE** . Pokud například výchozí země/oblast a jazyk hostitelského operačního systému jsou "USA" a "English", jsou následující dvě volání funkce **setlocale** funkčně ekvivalentní:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Další informace naleznete v tématu direktiva pragma [setlocale](../../preprocessor/setlocale.md) v [odkazu C/C++ preprocesor](../../preprocessor/c-cpp-preprocessor-reference.md).

Funkce [_configthreadlocale](configthreadlocale.md) slouží k řízení, zda má **setlocale** ovlivnit národní prostředí všech vláken v programu nebo pouze národní prostředí volajícího vlákna.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setlocale**|\<locale. h >|
|**_wsetlocale**|\<locale. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
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

## <a name="see-also"></a>Viz také

[Názvy národních prostředí, jazyky a řetězce země/oblasti](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale _wcreate_locale](create-locale-wcreate-locale.md)\
\ [národního prostředí](../../c-runtime-library/locale.md)
[localeconv](localeconv.md)\
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
\ [funkcí strcoll –](../../c-runtime-library/strcoll-functions.md)
[strftime, wcsftime, _strftime_l _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, Wcsxfrm, _strxfrm_l _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
