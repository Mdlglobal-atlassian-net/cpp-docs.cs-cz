---
title: setlocale –, _wsetlocale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46f523ba11902f3eaa74fc649791313ee9388824
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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

Pokud je to platná *národního prostředí* a *kategorie* , jsou vypsáni vrací ukazatel na řetězec přidružený k zadané *národního prostředí* a *kategorie*. Pokud *národního prostředí* nebo *kategorie* není platná, vrátí ukazatele null a aktuální nastavení národního prostředí programu, nebudou změněny.

Například volání

```C
setlocale( LC_ALL, "en-US" );
```

nastaví všechny kategorie, aby vracely pouze řetězec

```Output
en-US
```

Můžete zkopírovat řetězec vrácený **setlocale** obnovit část informací o národním prostředí programu. Globální nebo přístup z více vláken místní úložiště se používá pro řetězec vrácený **setlocale**. Novější volá, aby se **setlocale** přepsat řetězce, který by způsobila neplatnost ukazatele řetězec vrácený starší volání.

## <a name="remarks"></a>Poznámky

Použití **setlocale –** funkce nastavit, změnit nebo dotaz na některé nebo všechny informace aktuální národní prostředí programu určeného *národního prostředí* a *kategorie*. *národní prostředí* odkazuje na polohu (země nebo oblast a jazyk), pro které můžete přizpůsobit některé aspekty vašeho programu. Ke kategoriím závislým na národním prostředí patří formátování dat nebo zobrazovací formát pro peněžní hodnoty. Pokud nastavíte *národního prostředí* výchozí řetězec pro jazyk, který má více formulářů, které jsou podporovány ve vašem počítači, měli byste zkontrolovat **setlocale** vrátit hodnotu zobrazíte jazyk, který je v platnosti. Například pokud nastavíte *národního prostředí* "čínština" může být návratovou hodnotu "čínština (zjednodušená)" nebo "tradiční čínština".

**_wsetlocale** je verze široká charakterová **setlocale –**; *národního prostředí* argument a vrátí hodnotu **_wsetlocale** jsou široká charakterová řetězce. **_wsetlocale** a **setlocale** chovat jinak shodně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale –**|**setlocale**|**setlocale**|**_wsetlocale**|

*Kategorie* argument určuje části informací o národním prostředí programu, které se vztahuje. Makra pro *kategorie* a jsou částí programu, které mají vliv na následujícím způsobem:

|*kategorie* příznak|Ovlivňuje|
|-|-|
**LC_ALL –**|Všechny kategorie, jak je uvedeno dále.
**LC_COLLATE –**|**Strcoll –**, **_stricoll –**, **wcscoll –**, **_wcsicoll –**, **strxfrm –**, **_ strncoll –**, **_strnicoll –**, **_wcsncoll –**, **_wcsnicoll –**, a **wcsxfrm –** funkce.
**LC_CTYPE –**|Funkce znak zpracování (s výjimkou **IsDigit –**, **isxdigit –**, **mbstowcs –**, a **mbtowc –**, které jsou poškozena).
**LC_MONETARY –**|Informace o formátování měnovou vrácené **localeconv –** funkce.
**LC_NUMERIC –**|Desetinnou znak pro formátovaný výstup rutiny (například **printf**) pro převod dat rutiny a -peněžní formátování informace vrácené **localeconv –**. Kromě znak desetinné čárky **lc_numeric –** řetězec vrácený řízení oddělovače tisíců sady a seskupení [localeconv –](localeconv.md).
**LC_TIME –**|**STRFTIME –** a **wcsftime –** funkce.

Tato funkce ověřuje parametr kategorie. Pokud parametr kategorie není jedním z hodnoty uvedené v předchozí tabulce, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastaví funkci **errno** k **einval –** a vrátí **NULL**.

*Národního prostředí* argument je ukazatel na řetězec, který určuje národní prostředí. Informace o formátu *národního prostředí* argument, najdete v části [názvy národních prostředí, jazyků a řetězce zemí/oblastí](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Pokud *národního prostředí* bodů na prázdný řetězec, národní prostředí je definované implementací nativní prostředí. Hodnota **C** Určuje minimální prostředí vyhovující ANSI C překlad. **C** národního prostředí předpokládá, že všechny **char** datové typy jsou 1 bajtů a jeho hodnota je vždycky menší než 256.

Při spuštění programu se spustí ekvivalent následujícího příkazu:

`setlocale( LC_ALL, "C" );`

*Národního prostředí* argument může trvat název národního prostředí, jazyk řetězec, řetězec jazyka a kód země nebo oblasti, znakové stránky, nebo řetězec jazyka, kód země nebo oblasti a znaková stránka. Sada dostupných názvů národního prostředí, jazyků, kódů země/oblasti a znakových stránek obsahuje všechny prvky, které jsou podporovány v rozhraní API Windows NLS, kromě znakových stránek, které vyžadují více než dva bajty na znak, například UTF-7 a UTF-8. Pokud zadáte hodnotu kódu stránky ve formátu UTF-7 nebo UTF-8, **setlocale** se nezdaří, vrátí hodnotu NULL. Sada názvů národního prostředí podporuje **setlocale** jsou popsané v [názvy národních prostředí, jazyků a řetězce zemí/oblastí](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Sada jazyka a země nebo oblast řetězce nepodporuje **setlocale** jsou uvedeny v [řetězce jazyků](../../c-runtime-library/language-strings.md) a [řetězce zemí/oblastí](../../c-runtime-library/country-region-strings.md). Doporučujeme, abyste s ohledem na výkon a údržbu řetězců národního prostředí formu národního prostředí integrovali do kódu nebo serializovali do úložiště. U řetězců názvu národního prostředí je méně pravděpodobné, že aktualizací operačního systému dojde k jejich změně, než v případě formy pro název jazyka a země či oblasti.

Ukazatele null, který je předán jako *národního prostředí* argument určuje **setlocale** k dotazování místo nastavit mezinárodní prostředí. Pokud *národního prostředí* argument je ukazatel s hodnotou null, není změnit aktuální nastavení národního prostředí programu. Místo toho **setlocale** vrací ukazatel na řetězec, který je přidružen *kategorie* z aktuální národní prostředí vlákna. Pokud *kategorie* argument je **LC_ALL**, funkce vrátí řetězec, který označuje aktuální nastavení každou kategorii, oddělené středníky. Například sekvence volání

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

Následující příklady týkají **LC_ALL** kategorie. Každý z řetězců .OCP a .AKT lze použít místo čísla znakové stránky a určit tak výchozí znakovou stránku OEM nebo případně výchozí znakovou stránku ANSI pro uživatele.

- `setlocale( LC_ALL, "" );`

   Nastaví národní prostředí na výchozí hodnotu, což je výchozí znaková stránka ANSI pro uživatele získaná z operačního systému.

- `setlocale( LC_ALL, ".OCP" );`

   Explicitně nastaví národní prostředí na aktuální znakovou stránku OEM získanou z operačního systému.

- `setlocale( LC_ALL, ".ACP" );`

   Nastaví národní prostředí na znakovou stránku ANSI získanou z operačního systému.

- `setlocale( LC_ALL, "<localename>" );`

   Nastaví název národního prostředí, který je indikován národní prostředí  *\<localename >*.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Nastaví národní prostředí na jazyk a země nebo oblast indikován  *\<jazyk >* a  *\<země >*, společně s výchozí znakovou stránku získané z hostitele operační systém.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Nastaví indikován jazyka, země nebo oblast a znaková stránka národního prostředí  *\<jazyk >*,  *\<země >*, a  *\<code_page >* řetězce. Můžete použít různé kombinace jazyka, země/oblasti a znakové stránky. Například toto volání nastaví národní prostředí na hodnotu francouzština, Kanada se znakovou stránkou 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Toto volání nastaví národní prostředí na hodnotu francouzština, Kanada s výchozí znakovou stránkou ANSI:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Toto volání nastaví národní prostředí na hodnotu francouzština, Kanada s výchozí znakovou stránkou OEM:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Nastaví národní prostředí pro jazyk, který je indikován  *\<jazyk >* a používá výchozí zemi nebo oblasti pro určený jazyk a ANSI uživatele výchozí znaková stránka pro země nebo oblast získaný od hostitele operační systém. Například následující volání **setlocale** stejné funkce:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   S ohledem na výkon a údržbu doporučujeme použít první z uvedených forem.

- `setlocale( LC_ALL, ".<code_page>" );`

   Znaková stránka nastaví na hodnotu indikován *< code_page >*, společně s výchozí země nebo oblast a jazyk (podle definice hostitelského operačního systému) pro zadanou znakovou stránku.

Kategorie musí být buď **LC_ALL** nebo **LC_CTYPE –** k ovlivnění změnu znaková stránka. Například pokud výchozí země nebo oblast a jazyk operačního systému hostitele "USA" a "Anglickou", následující dva volá, aby se **setlocale** stejné funkce:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Další informace najdete v tématu [setlocale](../../preprocessor/setlocale.md) – Direktiva pragma v [referenční dokumentace jazyka C/C++ Preprocessor](../../preprocessor/c-cpp-preprocessor-reference.md).

Funkce [_configthreadlocale –](configthreadlocale.md) je slouží ke kontrole, jestli **setlocale** ovlivní národního prostředí všechna vlákna v programu nebo pouze národního prostředí volající vlákno.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**setlocale**|\<Locale.h >|
|**_wsetlocale**|\<Locale.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Názvy národních prostředí, jazyků a řetězce zemí/oblastí](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
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
