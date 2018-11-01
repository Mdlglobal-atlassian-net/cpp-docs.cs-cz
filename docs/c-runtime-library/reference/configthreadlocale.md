---
title: _configthreadlocale
ms.date: 11/04/2016
apiname:
- _configthreadlocale
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
- _configthreadlocale
- configthreadlocale
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
ms.openlocfilehash: 244ef9ce93e39bef23a9d5d6792a10ca25355f5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648380"
---
# <a name="configthreadlocale"></a>_configthreadlocale

Nastaví možnosti národního prostředí pro vlákno.

## <a name="syntax"></a>Syntaxe

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Parametry

*per_thread_locale_type*<br/>
Možnost nastavit. Jedna z možností uvedených v následující tabulce.

## <a name="return-value"></a>Návratová hodnota

Předchozí stav národního prostředí pro vlákno (**_DISABLE_PER_THREAD_LOCALE** nebo **_ENABLE_PER_THREAD_LOCALE**), nebo hodnota -1 při selhání.

## <a name="remarks"></a>Poznámky

**_Configurethreadlocale** funkce se používá k řízení používání národní prostředí specifické pro vlákno. Použijte jednu z těchto *per_thread_locale_type* možností k určení stavu národního prostředí pro vlákno:

|||
|-|-|
**_ENABLE_PER_THREAD_LOCALE**|Zkontrolujte aktuální národní prostředí pro vlákno použijte specifické pro vlákno. Následující volání **setlocale** v tomto vlákně ovlivňují pouze vlastní národní prostředí vlákna.
**_DISABLE_PER_THREAD_LOCALE**|Zkontrolujte aktuální vlákno používalo globální národní prostředí. Následující volání **setlocale** v tomto vlákně ovlivňují ostatní vlákna používající globální národní prostředí.
**0**|Načte aktuální nastavení pro toto konkrétní vlákno.

Tyto funkce ovlivňují chování **setlocale**, **_tsetlocale –**, **_wsetlocale**, a **_setmbcp**. Pokud je národní prostředí pro vlákno zakázáno, všechna následná volání **setlocale** nebo **_wsetlocale** změní národní prostředí všech vláken, které používají globální národní prostředí. Když je povoleno národní prostředí pro vlákno, **setlocale** nebo **_wsetlocale** ovlivní pouze národního prostředí aktuálního vlákna.

Pokud používáte **_configurethreadlocale** k povolení národního prostředí pro vlákno, doporučujeme vám, že zavoláte **setlocale** nebo **_wsetlocale** k nastavení upřednostňovaného národního prostředí v tomto vlákně ihned poté.

Pokud *per_thread_locale_type* není jedna z hodnot uvedených v tabulce, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_configthreadlocale**|\<Locale.h >|

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

## <a name="see-also"></a>Viz také:

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Multithreading a národní prostředí](../../parallel/multithreading-and-locales.md)<br/>
