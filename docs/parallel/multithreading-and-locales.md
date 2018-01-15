---
title: "Multithreading a národní prostředí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e60235bb011cb130b06a51a498cd8b5b88a56232
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-and-locales"></a>Multithreading a národní prostředí
Běhové knihovny jazyka C a standardní knihovny C++ poskytují podporu pro změnu národního prostředí vašeho programu. Toto téma popisuje problémy, které nastat při použití funkce národního prostředí obou knihoven v aplikaci s více vlákny.  
  
## <a name="remarks"></a>Poznámky  
 S běhové knihovny, můžete vytvořit vícevláknové aplikace pomocí `_beginthread` a `_beginthreadex` funkce. Toto téma popisuje pouze vícevláknové aplikace vytvořené pomocí těchto funkcí. Další informace najdete v tématu [_beginthread _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
 Můžete změnit národní prostředí pomocí běhové knihovny jazyka C [setlocale](../preprocessor/setlocale.md) funkce. V předchozích verzích Visual C++ tato funkce by měla vždy změnit národního prostředí v celé aplikaci. Nyní je zde podpora pro nastavení národního prostředí na základě vlákna. To se provádí pomocí [_configthreadlocale –](../c-runtime-library/reference/configthreadlocale.md) funkce. Chcete-li určit, že [setlocale](../preprocessor/setlocale.md) by se měl změnit pouze národního prostředí v aktuální vlákno volání `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` v daném vláknu. Naopak volání `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` způsobí, že vlákno pro použití jako globální národní prostředí a všechny volání [setlocale](../preprocessor/setlocale.md) v tom, že vlákno změní národní prostředí v všechna vlákna, které explicitně nepovolili národní prostředí podle vláken.  
  
 Můžete změnit národní prostředí pomocí běhové knihovny jazyka C++ [locale – třída](../standard-library/locale-class.md). Při volání [locale::global](../standard-library/locale-class.md#global) metoda, změníte národní prostředí v každé vlákno, které explicitně nepovolil národní prostředí podle vláken. Chcete-li změnit národního prostředí v jedno vlákno nebo část aplikace, stačí vytvořit instanci `locale` objekt v daném vlákně nebo části kódu.  
  
> [!NOTE]
>  Volání metody [locale::global](../standard-library/locale-class.md#global) změní národní prostředí pro standardní knihovna C++ a běhové knihovny jazyka C. Avšak volání [setlocale](../preprocessor/setlocale.md) pouze změny národní prostředí běhové knihovny jazyka C; standardní knihovna C++ nemá vliv.  
  
 Následující příklady ukazují, jak používat [setlocale](../preprocessor/setlocale.md) funkce, [locale – třída](../standard-library/locale-class.md)a [_configthreadlocale –](../c-runtime-library/reference/configthreadlocale.md) funkce změnit národní prostředí aplikace několika různých scénářů.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu hlavní vlákno dva potomky. První vlákno, vlákna A, povoluje národní prostředí podle vláken voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhý vlákno, vlákno B, jakož i hlavní vlákno, nepovolujte národní prostředí podle vláken. Přístup z více vláken poté provede změny národního prostředí pomocí [setlocale](../preprocessor/setlocale.md) funkce běhové knihovny jazyka C.  
  
 Má povoleno, národní prostředí podle vláken pouze tyto funkce běhové knihovny jazyka C v přístup z více vláken A začít používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C v vlákno B a hlavního vlákna nadále používat národního prostředí "C". Navíc od [setlocale](../preprocessor/setlocale.md) nemá vliv na národním prostředí standardní knihovna C++, všechny standardní knihovna C++ objekty nadále používat národního prostředí "C".  
  
```  
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
 V tomto příkladu hlavní vlákno dva potomky. První vlákno, vlákna A, povoluje národní prostředí podle vláken voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhý vlákno, vlákno B, jakož i hlavní vlákno, nepovolujte národní prostředí podle vláken. Přístup z více vláken A poté provede změny použitím národního prostředí [locale::global](../standard-library/locale-class.md#global) metoda standardní knihovny jazyka C++.  
  
 Má povoleno, národní prostředí podle vláken pouze tyto funkce běhové knihovny jazyka C v přístup z více vláken A začít používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C v vlákno B a hlavního vlákna nadále používat národního prostředí "C". Ale protože [locale::global](../standard-library/locale-class.md#global) metoda změní národního prostředí "globální", všechny objekty standardní knihovna C++ v všechna vlákna začít používat "Francouzské" národní prostředí.  
  
```  
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
 V tomto příkladu hlavní vlákno dva potomky. První vlákno, vlákna A, povoluje národní prostředí podle vláken voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhý vlákno, vlákno B, jakož i hlavní vlákno, nepovolujte národní prostředí podle vláken. Přístup z více vláken B poté provede změny národního prostředí pomocí [setlocale](../preprocessor/setlocale.md) funkce běhové knihovny jazyka C.  
  
 Vzhledem k tomu, že vlákno B nemá povoleno národní prostředí podle vláken, funkce běhové knihovny jazyka C v vlákno B a hlavního vlákna začít používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C v pokračovat přístup z více vláken A použít národního prostředí "C", protože přístup z více vláken A má povoleno národní prostředí podle vláken. Navíc od [setlocale](../preprocessor/setlocale.md) nemá vliv na národním prostředí standardní knihovna C++, všechny standardní knihovna C++ objekty nadále používat národního prostředí "C".  
  
```  
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
 V tomto příkladu hlavní vlákno dva potomky. První vlákno, vlákna A, povoluje národní prostředí podle vláken voláním `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)`. Druhý vlákno, vlákno B, jakož i hlavní vlákno, nepovolujte národní prostředí podle vláken. Přístup z více vláken B pak provede změny použitím národního prostředí [locale::global](../standard-library/locale-class.md#global) metoda standardní knihovny jazyka C++.  
  
 Vzhledem k tomu, že vlákno B nemá povoleno národní prostředí podle vláken, funkce běhové knihovny jazyka C v vlákno B a hlavního vlákna začít používat "Francouzské" národní prostředí. Funkce běhové knihovny jazyka C v pokračovat přístup z více vláken A použít národního prostředí "C", protože přístup z více vláken A má povoleno národní prostředí podle vláken. Ale protože [locale::global](../standard-library/locale-class.md#global) metoda změní národního prostředí "globální", všechny objekty standardní knihovna C++ v všechna vlákna začít používat "Francouzské" národní prostředí.  
  
```  
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
 [Podpora více vláken ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [_beginthread –, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [_configthreadlocale –](../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale –](../preprocessor/setlocale.md)   
 [Internacionalizace](../c-runtime-library/internationalization.md)   
 [Národní prostředí](../c-runtime-library/locale.md)   
 [\<clocale – >](../standard-library/clocale.md)   
 [\<národní prostředí >](../standard-library/locale.md)   
 [locale – třída](../standard-library/locale-class.md)