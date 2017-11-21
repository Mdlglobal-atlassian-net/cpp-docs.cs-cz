---
title: "strtok_s –, _strtok_s_l –, wcstok_s –, _wcstok_s_l –, _mbstok_s –, _mbstok_s_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
dev_langs: C++
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fd0738d1a08eb0c2285f12314770ec1120e7d97
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Vyhledá další token v řetězci pomocí aktuálního národního prostředí nebo pomocí předaného národního prostředí. Tyto verze nástroje [strtok –, _strtok_l –, wcstok –, _wcstok_l –, _mbstok –, _mbstok_l –](../../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbstok_s`a `_mbstok_s_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```
char* strtok_s(  
   char* str,  
   const char* delimiters,  
   char** context  
);

char* _strtok_s_l(  
   char* str,  
   const char* delimiters,  
   char** context,  
   _locale_t locale  
);  

wchar_t* wcstok_s(  
   wchar_t* str,  
   const wchar_t* delimiters,   
   wchar_t** context  
); 
 
wchar_t *_wcstok_s_l(  
   wchar_t* str,  
   const wchar_t* delimiters,   
   wchar_t** context,  
   _locale_t locale  
);  

unsigned char* _mbstok_s(  
   unsigned char* str,  
   const unsigned char* delimiters,   
   char** context  
);  

unsigned char* _mbstok_s(  
   unsigned char* str,  
   const unsigned char* delimiters,   
   char** context,  
   _locale_t locale  
);  
```  
  
### <a name="parameters"></a>Parametry  

*str –*  
Řetězec obsahující tokeny najít.  
  
*oddělovače*  
Sada oddělovač znaků se má použít.  
  
*kontext*  
Slouží k ukládání informací pozici mezi volání funkce.  
  
*národní prostředí*  
Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  

Vrátí ukazatel na další token nalezen v *str*. Vrátí `NULL` při nebyly nalezeny žádné další tokeny. Každé volání upraví *str* nahrazením `NULL` znak pro první oddělovač, který se nachází po vrácený token.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|*str –*|*oddělovače*|*kontext*|Návratová hodnota|`errno`|  
|----------------|------------------|---------------|------------------|-------------|  
|`NULL`|všechny|ukazatel na ukazatel s hodnotou null|`NULL`|`EINVAL`|  
|všechny|`NULL`|všechny|`NULL`|`EINVAL`|  
|všechny|všechny|`NULL`|`NULL`|`EINVAL`|  
  
Pokud *str* je `NULL` ale *kontextu* ukazatel na ukazatel platný kontext, se nezobrazí žádná chyba.  
  
## <a name="remarks"></a>Poznámky  

`strtok_s` Řady funkcí vyhledá na další token v *str*. Sadu znaků *oddělovače* Určuje možné oddělovače token, který má být nalezena v *str* v aktuálním volání. `wcstok_s`a `_mbstok_s` jsou široká charakterová a vícebajtových znaků verze `strtok_s`. Argumenty a vrácené hodnoty funkcí `wcstok_s` a `_wcstok_s_l` jsou širokoznaké řetězce. Argumenty a vrácené hodnoty funkcí `_mbstok_s` a `_mbstok_s_l` jsou vícebajtové znakové řetězce. Tyto funkce chovají stejně jako jinak.  

Tato funkce ověří jeho parametry. Pokud dojde k chybový stav, stejně jako chybové stavy tabulky, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `NULL`.

Při prvním volání `strtok_s` funkce Přeskočí úvodní oddělovače a vrací ukazatel na první token v *str*, ukončení token s znak hodnoty null. Další tokeny, lze zjistit mimo zbytek *str* řadou volání `strtok_s`. Každé volání `strtok_s` upraví *str* vložením znak hodnoty null po token vrácený toto volání. *Kontextu* ukazatel uchovává informace o řetězce, který je načítán a kde v řetězci na další token je možné načíst. Ke čtení na další token z *str*, volání `strtok_s` s `NULL` hodnota *str* argument a předejte stejné *kontextu* parametr. `NULL` *Str* argument příčiny `strtok_s` pro vyhledávání na další token v upravenou *str*. *Oddělovače* argument může trvat libovolná hodnota od jednoho volání na další, tak, aby sada oddělovače se může lišit.

Vzhledem k tomu *kontextu* parametr nahrazuje statické vyrovnávacích pamětí, používaných v `strtok` a `_strtok_l`, je možné analyzovat dva řetězce současně ve stejném vlákně, v.

Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez `_l` příponu použít aktuální národní prostředí vlákna pro toto chování závislých na národním prostředí. Verze se `_l` příponu jsou shodné s tím rozdílem, že místo toho používají *národního prostředí* parametr. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strtok_s`|\<String.h >|
|`_strtok_s_l`|\<String.h >|
|`wcstok_s`,<br />`_wcstok_s_l`|\<String.h > nebo \<wchar.h >|
|`_mbstok_s`,<br />`_mbstok_s_l`|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|\_UNICODE & \_MBCS není definován|\_MBCS definované|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcstok_s`|`strtok_s`|`_mbstok_s`|`wcstok_s`|
|`_tcstok_s_l`|`_strtok_s_l`|`_mbstok_s_l`|`_wcstok_s_l`|

## <a name="example"></a>Příklad

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```  
  
```Output  
Tokens:  
 A  
        Another  
 string  
        string  
 of  
        parsed  
 tokens  
        at  
 and  
        the  
 some  
        same  
 more  
        time.  
 tokens  
```  
  
## <a name="see-also"></a>Viz také  

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)  
[Národní prostředí](../../c-runtime-library/locale.md)  
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)  
[strcspn –, wcscspn –, _mbscspn –, _mbscspn_l –](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)  
[strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)