---
title: "_configthreadlocale – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c12a60cb56373958f8e467b3a1ec3f6e4ff82c0b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="configthreadlocale"></a>_configthreadlocale
Nakonfiguruje možnosti národní prostředí podle vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _configthreadlocale(  
   int type  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `type`  
 Možnost nastavit. Jednu z možností uvedených v následující tabulce.  
  
## <a name="return-value"></a>Návratová hodnota  
 Předchozí stav národní prostředí podle vláken (`_DISABLE_PER_THREAD_LOCALE` nebo `_ENABLE_PER_THREAD_LOCALE`), nebo -1 při selhání.  
  
## <a name="remarks"></a>Poznámky  
 `_configurethreadlocale` Funkce slouží k řízení použití specifické pro vlákno národní prostředí. Určuje stav národní prostředí podle vláken, použijte jednu z těchto možností:  
  
 `_ENABLE_PER_THREAD_LOCALE`  
 Zkontrolujte aktuální národní prostředí vlákna použití konkrétního přístup z více vláken. Následující volání `setlocale` ve tohoto podprocesu vliv pouze národní prostředí vlákna je vlastní.  
  
 `_DISABLE_PER_THREAD_LOCALE`  
 Zkontrolujte aktuální vlákno použít globální národní prostředí. Následující volání `setlocale` ve tohoto podprocesu vliv jiná vlákna pomocí globální národní prostředí.  
  
 `0`  
 Načte aktuální nastavení pro tuto konkrétní přístup z více vláken.  
  
 Tyto funkce ovlivnit chování `setlocale`, `_tsetlocale`, `_wsetlocale`, a `_setmbcp`. Pokud národní prostředí podle vláken je zakázáno, všechny následné volání `setlocale` nebo `_wsetlocale` změní národní prostředí všechna vlákna, které používají globální národní prostředí. Pokud je povoleno národní prostředí podle vláken, `setlocale` nebo `_wsetlocale` ovlivňuje pouze národního prostředí aktuálního vlákna.  
  
 Pokud používáte `_configurethreadlocale` , aby národní prostředí podle vláken, doporučujeme volat `setlocale` nebo `_wsetlocale` nastavit upřednostňované národního prostředí v daném vláknu hned potom.  
  
 Pokud `type` není jedním z hodnoty uvedené v tabulce, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí hodnotu -1.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_configthreadlocale`|\<Locale.h >|  
  
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
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Multithreading a národní prostředí](../../parallel/multithreading-and-locales.md)  
