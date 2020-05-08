---
title: _configthreadlocale
ms.date: 4/2/2020
api_name:
- _configthreadlocale
- _o__configthreadlocale
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _configthreadlocale
- configthreadlocale
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
ms.openlocfilehash: 26bcfe0d93a8c2b1a14e6afc0d413a5c7e4a7f6e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917310"
---
# <a name="_configthreadlocale"></a>_configthreadlocale

Konfiguruje možnosti národního prostředí pro vlákno.

## <a name="syntax"></a>Syntaxe

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Parametry

*per_thread_locale_type*<br/>
Možnost, kterou chcete nastavit. Jedna z možností uvedených v následující tabulce.

## <a name="return-value"></a>Návratová hodnota

Předchozí stav národního prostředí pro vlákno (**_DISABLE_PER_THREAD_LOCALE** nebo **_ENABLE_PER_THREAD_LOCALE**) nebo-1 při selhání.

## <a name="remarks"></a>Poznámky

Funkce **_configurethreadlocale** slouží k řízení použití národních prostředí specifických pro vlákno. Použijte jednu z těchto možností *per_thread_locale_type* k určení nebo určení stavu národního prostředí pro vlákno:

| Možnost | Popis |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | Nastaví aktuální vlákno pro použití národního prostředí specifického pro vlákno. Následná volání funkce **setlocale** v tomto vlákně ovlivňují pouze vlastní národní prostředí vlákna. |
| **_DISABLE_PER_THREAD_LOCALE** | Nastaví aktuální vlákno na používání globálního národního prostředí. Následná volání funkce **setlocale** v tomto vlákně ovlivňují jiná vlákna pomocí globálního národního prostředí. |
| **0** | Načte aktuální nastavení tohoto konkrétního vlákna. |

Tyto funkce mají vliv na chování funkce **setlocale**, **_tsetlocale**, **_wsetlocale**a **_setmbcp**. Když je národní prostředí pro vlákno zakázané, jakékoli následné volání metody **setlocale** nebo **_wsetlocale** mění národní prostředí všech vláken, která používají globální národní prostředí. Pokud je povoleno národní prostředí pro vlákno, příkaz **setlocale** nebo **_wsetlocale** ovlivní pouze národní prostředí aktuálního vlákna.

Použijete-li **_configurethreadlocale** pro povolení národního prostředí pro vlákno, doporučujeme, abyste voláním **setlocale** nebo **_wsetlocale** nastavili upřednostňované národní prostředí v tomto vlákně hned následně.

Pokud *per_thread_locale_type* není jednou z hodnot uvedených v tabulce, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí-1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_configthreadlocale**|\<locale. h>|

## <a name="example"></a>Příklad

```cpp
// crt_configthreadlocale.cpp
//
// This program demonstrates the use of _configthreadlocale when
// using two independent threads.
//
// Compile by using: cl /EHsc /W4 crt_configthreadlocale.cpp

#include <locale.h>
#include <mbctype.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date and time in the current
// locale's format.
int get_time(unsigned char* str)
{
    __time64_t  ltime;
    struct tm   thetime;

    // Retieve the time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // using %#x is the long date representation,
    // appropriate to the current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm*)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to German
// and prints the time.
unsigned __stdcall SecondThreadFunc( void* /*pArguments*/ )
{
    unsigned char str[BUFF_SIZE];

    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the thread code page
    _setmbcp(_MB_CP_ANSI);

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "German"));

    // Retrieve the time string from the helper function
    if (get_time(str) == 0)
    {
        printf("The time in German locale is: '%s'\n", str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread spawns a second thread (above) and then
// sets the locale to English and prints the time.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Retrieve the time string from the helper function
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "English"));

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      NULL, 0, &threadID );

    if (get_time(str) == 0)
    {
        // Retrieve the time string from the helper function
        printf("The time in English locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to English_United States.1252.
The time in English locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to German_Germany.1252.
The time in German locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Viz také

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Multithreading a národní prostředí](../../parallel/multithreading-and-locales.md)<br/>
