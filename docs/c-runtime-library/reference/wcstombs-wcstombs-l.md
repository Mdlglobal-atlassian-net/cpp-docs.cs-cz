---
title: "wcstombs –, _wcstombs_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcstombs
- _wcstombs_l
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
f1_keywords:
- wcstombs
- _wcstombs_l
dev_langs:
- C++
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7d0a5fa1fd7eb869602d8428a7cc087174739a1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l
Převede posloupnost široké znaky na odpovídající posloupnost více-bajtové znaky. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [wcstombs_s –, _wcstombs_s_l –](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `mbstr`  
 Adresa posloupnost více-bajtové znaky.  
  
 `wcstr`  
 Adresa posloupnost široké znaky.  
  
 `count`  
 Maximální počet bajtů, které mohou být uloženy ve více-bajtové výstupní řetězec.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud `wcstombs` úspěšně převede vícebajtové řetězce, vrátí počet bajtů zapsaných do řetězce vícebajtových výstup, s výjimkou ukončení `NULL` (pokud existuje). Pokud `mbstr` argument je `NULL`, `wcstombs` vrátí požadovaná velikost v bajtech cílový řetězec. Pokud `wcstombs` zaznamená široká znaková nelze převést na vícebajtových znaků, vrátí hodnotu -1 přetypovat na typ `size_t` a nastaví `errno` k `EILSEQ`.  
  
## <a name="remarks"></a>Poznámky  
 `wcstombs` Funkce převede řetězec široká charakterová, na kterou odkazuje `wcstr` na odpovídající vícebajtových znaků a ukládá výsledky do `mbstr` pole. `count` Určuje maximální počet bajtů, které mohou být uloženy v řetězci vícebajtové výstup (to znamená, velikost `mbstr`). Obecně platí není znám, kolik bajtů se bude vyžadovat při převodu řetězce široká charakterová. Některé široké znaky bude vyžadovat pouze jeden bajt do výstupního řetězce; jiné vyžadují dva. Pokud jsou dva bajty v vícebajtové výstupní řetězec pro každý široké znak ve vstupním řetězci (včetně široká znaková `NULL`), výsledek záruku, že se nevešla.  
  
 Pokud `wcstombs` zaznamená znak hodnoty null široká charakterová (L '\0') před nebo po `count` dojde, převede ji 0 8bitové a zastaví se. Proto řetězce vícebajtových znaků na `mbstr` je ukončené hodnotou null jenom v případě `wcstombs` širokého znaku prázdný znak, zaznamená při převodu. Pokud daná pořadí na kterou odkazuje `wcstr` a `mbstr` překrývají, chování `wcstombs` není definován.  
  
 Pokud `mbstr` argument je `NULL`, `wcstombs` vrátí požadovaná velikost v bajtech cílový řetězec.  
  
 `wcstombs` ověří jeho parametry. Pokud `wcstr` je `NULL`, nebo pokud `count` je větší než `INT_MAX`, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, nastaví funkci `errno` k `EINVAL` a vrátí hodnotu -1.  
  
 `wcstombs` používá aktuální národní prostředí pro chování všech závislých na národním prostředí; `_wcstombs_l` se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`wcstombs`|\<stdlib.h>|  
|`_wcstombs_l`|\<stdlib.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Tento program znázorňuje chování `wcstombs` funkce.  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 13  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)