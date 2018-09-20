---
title: Multithreading a národní prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d728bb8696a71eb733f15c236e42dc1859c5f135
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428782"
---
# <a name="multithreading-and-locales"></a>Multithreading a národní prostředí

Běhové knihovny jazyka C a standardní knihovny C++ poskytují podporu pro změnu národního prostředí programu. Toto téma popisuje problémy, které vznikají při použití funkce národního prostředí obě knihovny ve vícevláknových aplikacích.

## <a name="remarks"></a>Poznámky

S běhové knihovny jazyka C, můžete vytvořit vícevláknové aplikace pomocí `_beginthread` a `_beginthreadex` funkce. Toto téma popisuje pouze vícevláknové aplikace vytvořené pomocí těchto funkcí. Další informace najdete v tématu [_beginthread _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).

Chcete-li změnit národní prostředí pomocí běhové knihovny jazyka C, použijte [setlocale](../preprocessor/setlocale.md) funkce. V předchozích verzích aplikace Visual C++ tato funkce by měla vždy změnit národní prostředí v celé aplikaci. Je teď podporují pro nastavení národního prostředí na základě vlákno. To se provádí pomocí [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) funkce. Chcete-li určit, že [setlocale](../preprocessor/setlocale.md) by měl změnit pouze národní prostředí v aktuálním vlákně, volání `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` v tomto vlákně. Naopak volání `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` způsobí, že toto vlákno pro použití globální národní prostředí a voláním [setlocale](../preprocessor/setlocale.md) v tom, že vlákno se změní národní prostředí ve všech vláknech, které nejsou explicitně povolená národní prostředí pro vlákno.

Chcete-li změnit národní prostředí pomocí knihovny Runtime jazyka C++, použijte [locale – třída](../standard-library/locale-class.md). Při volání [locale::global](../standard-library/locale-class.md#global) metodu, můžete změnit národní prostředí v každém vlákně, které explicitně nepovolil národní prostředí pro vlákno. Chcete-li změnit národní prostředí v jednom vlákně nebo část aplikace, jednoduše vytvořit instanci `locale` objekt vlákna nebo části kódu.

> [!NOTE]
> Volání [locale::global](../standard-library/locale-class.md#global) změní národní prostředí pro standardní knihovny C++ a C Runtime Library. Však voláním [setlocale](../preprocessor/setlocale.md) pouze změny národního prostředí běhové knihovny jazyka C; standardní knihovny C++ není ovlivněno.

Následující příklady ukazují, jak používat [setlocale](../preprocessor/setlocale.md) funkce, [locale – třída](../standard-library/locale-class.md)a [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) funkce Změna národního prostředí aplikace několik různých scénářů.

## <a name="example"></a>Příklad

V tomto příkladu hlavního vlákna dva potomky. První vlákno, vlákno A povoluje národní prostředí pro vlákno voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhé vlákno, vlákno B, jakož i hlavním vlákně, nepovolujte národní prostředí pro vlákno. Vlákna A poté pokračuje změnit pomocí národního prostředí [setlocale](../preprocessor/setlocale.md) funkce běhové knihovny jazyka C.

Protože má povoleno, národní prostředí vlákna pouze na funkce běhové knihovny jazyka C ve vlákně A začněte používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C ve vlákně B a v hlavním vlákně dál používají národní prostředí "C". Navíc protože [setlocale](../preprocessor/setlocale.md) nemá vliv na národní prostředí standardní knihovny C++, všechny standardní knihovny C++ objekty i nadále používat národní prostředí "C".

```cpp
// multithread_locale_1.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "C"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>Příklad

V tomto příkladu hlavního vlákna dva potomky. První vlákno, vlákno A povoluje národní prostředí pro vlákno voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhé vlákno, vlákno B, jakož i hlavním vlákně, nepovolujte národní prostředí pro vlákno. Vlákna A poté pokračuje změnit pomocí národního prostředí [locale::global](../standard-library/locale-class.md#global) metoda standardní knihovny C++.

Protože má povoleno, národní prostředí vlákna pouze na funkce běhové knihovny jazyka C ve vlákně A začněte používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C ve vlákně B a v hlavním vlákně dál používají národní prostředí "C". Ale protože [locale::global](../standard-library/locale-class.md#global) metoda změní národní prostředí "globální", všechny objekty standardní knihovny jazyka C++ ve všech vláknech začít používat "Francouzské" národní prostředí.

```cpp
// multithread_locale_2.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "French_France.1252"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="example"></a>Příklad

V tomto příkladu hlavního vlákna dva potomky. První vlákno, vlákno A povoluje národní prostředí pro vlákno voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhé vlákno, vlákno B, jakož i hlavním vlákně, nepovolujte národní prostředí pro vlákno. Vlákno B poté provede změny pomocí národního prostředí [setlocale](../preprocessor/setlocale.md) funkce běhové knihovny jazyka C.

Protože B vlákna nemá povoleno národní prostředí pro vlákno, funkce běhové knihovny jazyka C ve vlákně B a v hlavním vlákně začít používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C v vlákna A nadále používat národní prostředí "C", protože má povoleno národní prostředí pro vlákno. Navíc protože [setlocale](../preprocessor/setlocale.md) nemá vliv na národní prostředí standardní knihovny C++, všechny standardní knihovny C++ objekty i nadále používat národní prostředí "C".

```cpp
// multithread_locale_3.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "C"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "C"
```

## <a name="example"></a>Příklad

V tomto příkladu hlavního vlákna dva potomky. První vlákno, vlákno A povoluje národní prostředí pro vlákno voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhé vlákno, vlákno B, jakož i hlavním vlákně, nepovolujte národní prostředí pro vlákno. Vlákno B poté provede změny pomocí národního prostředí [locale::global](../standard-library/locale-class.md#global) metoda standardní knihovny C++.

Protože B vlákna nemá povoleno národní prostředí pro vlákno, funkce běhové knihovny jazyka C ve vlákně B a v hlavním vlákně začít používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C v vlákna A nadále používat národní prostředí "C", protože má povoleno národní prostředí pro vlákno. Ale protože [locale::global](../standard-library/locale-class.md#global) metoda změní národní prostředí "globální", všechny objekty standardní knihovny jazyka C++ ve všech vláknech začít používat "Francouzské" národní prostředí.

```cpp
// multithread_locale_4.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "French_France.1252"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="see-also"></a>Viz také

[Podpora multithreadingu ve starším kódu (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)<br/>
[setlocale](../preprocessor/setlocale.md)<br/>
[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Národní prostředí](../c-runtime-library/locale.md)<br/>
[\<clocale – >](../standard-library/clocale.md)<br/>
[\<národní prostředí >](../standard-library/locale.md)<br/>
[locale – třída](../standard-library/locale-class.md)