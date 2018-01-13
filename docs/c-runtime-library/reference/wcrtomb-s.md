---
title: "wcrtomb_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wcrtomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords: wcrtomb_s
dev_langs: C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13134a3e6b34be13d6d878cf94f204bb6c87a458
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="wcrtombs"></a>wcrtomb_s
Široká znaková převeďte do reprezentace vícebajtových znaků. Verzi [wcrtomb –](../../c-runtime-library/reference/wcrtomb.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char *mbchar,  
   size_t sizeOfmbchar,  
   wchar_t *wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char (&mbchar)[size],  
   wchar_t *wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pReturnValue`  
 Vrátí počet bajtů zapsaných nebo -1, pokud došlo k chybě.  
  
 [out]`mbchar`  
 Převést výsledné vícebajtových znaků.  
  
 [v]`sizeOfmbchar`  
 Velikost `mbchar` proměnné v bajtech.  
  
 [v]`wchar`  
 Široká znaková převést.  
  
 [v]`mbstate`  
 Ukazatel na `mbstate_t` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nula nebo `errno` hodnotu, pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `wcrtomb_s` Funkce převede široký znak, od ve stavu zadanou konverzi obsažené v `mbstate`, z hodnoty obsažené v `wchar`, do adresu reprezentována `mbchar`. `pReturnValue` Bude použita hodnota počet bajtů převést, ale ne víc než `MB_CUR_MAX` bajtů nebo -1, pokud došlo k chybě.  
  
 Pokud `mbstate` má hodnotu null, interní `mbstate_t` převod stavu se používá. Pokud je znak obsažené v `wchar` nemá odpovídající vícebajtových znaků, hodnota `pReturnValue` bude mít hodnotu -1 a vrátí funkce `errno` hodnotu `EILSEQ`.  
  
 `wcrtomb_s` Funkce se liší od [wctomb_s –, _wctomb_s_l –](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md) podle jeho restartability. Stav převodu je uložený ve `mbstate` pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování. Například byste použili aplikaci `wcsrlen` místo `wcslen`, pokud následných volání `wcsrtombs_s` používaly místo`wcstombs_s.`  
  
 V jazyce C++ pomocí této funkce se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Výjimky  
 `wcrtomb_s` Tak dlouho, dokud volání funkce neexistuje v aktuální vlákno je funkce s více vlákny bezpečné `setlocale` průběhu této funkce je provádění a `mbstate` má hodnotu null.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_wcrtomb_s.c  
// This program converts a wide character  
// to its corresponding multibyte character.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    errno_t     returnValue;  
    size_t      pReturnValue;  
    mbstate_t   mbstate;  
    size_t      sizeOfmbStr = 1;  
    char        mbchar = 0;  
    wchar_t*    wchar = L"Q\0";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),  
                            *wchar, &mbstate);  
    if (returnValue == 0) {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wchar);  
        printf(" was converted to a the \"%c\" ", mbchar);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
```Output  
The corresponding wide character "Q" was converted to a the "Q" multibyte character.  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`wcrtomb_s`|\<wchar.h >|  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)