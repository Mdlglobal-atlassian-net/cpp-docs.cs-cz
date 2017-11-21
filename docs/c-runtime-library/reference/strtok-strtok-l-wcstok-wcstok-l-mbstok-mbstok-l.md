---
title: "strtok –, _strtok_l –, wcstok –, _wcstok_l –, _mbstok –, _mbstok_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
- _mbstok
- strtok
- _tcstok
- wcstok
dev_langs: C++
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
caps.latest.revision: "34"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e41fb5edc039b1d1bb98bfee48a234c9d4c8f62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strtok-strtokl-wcstok-wcstokl-mbstok-mbstokl"></a>strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l
Vyhledá na další token v řetězci, pomocí aktuální národní prostředí nebo zadaný národní prostředí, který se předává v. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [strtok_s –, _strtok_s_l –, wcstok_s –, _wcstok_s_l –, _mbstok_s –, _mbstok_s_l –](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md).  
  
> [!IMPORTANT]
>  `_mbstok`a `_mbstok_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *strtok(  
   char *strToken,  
   const char *strDelimit   
);  
wchar_t *wcstok(  
   wchar_t *strToken,  
   const wchar_t *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `strToken`  
 Řetězec obsahující token nebo tokeny.  
  
 `strDelimit`  
 Sada oddělovacích znaků.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na další token v parametru `strToken`. Vrátí hodnotu `NULL`, pokud nejsou nalezeny žádné další tokeny. Každé volání upraví parametr `strToken` nahrazením znaku `NULL` prvního oddělovače, který se objeví po vráceném tokenu.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `strtok` vyhledá další token v parametru `strToken`. Množina znaků v parametru `strDelimit` určuje možné oddělovače tokenu, který má být nalezen v parametru `strToken` při aktuálním volání. `wcstok`a `_mbstok` jsou široká charakterová a vícebajtových znaků verze `strtok`. Argumenty a vrací hodnotu `wcstok` jsou široká charakterová řetězce; u `_mbstok` jsou řetězců vícebajtových znaků. Tyto tři funkce chovají stejně jako jinak.  
  
> [!IMPORTANT]
>  Tyto funkce zpoplatněná potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti problémy jsou často metodu systému útoku, výsledkem bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Při prvním volání `strtok`, funkce Přeskočí úvodní oddělovače a vrací ukazatel na první token v `strToken`, ukončení token s znak hodnoty null. Další tokeny lze zjistit ze zbytku parametru `strToken` řadou volání funkce `strtok`. Každé volání `strtok` upraví `strToken` vložením znak hodnoty null po `token` vrácený toto volání. Ke čtení na další token z `strToken`, volání `strtok` s `NULL` hodnota `strToken` argument. `NULL` `strToken` Argument příčiny `strtok` pro vyhledávání na další token v upravenou `strToken`. Argument `strDelimit` přijímá jakoukoli hodnotu z jednoho volání na další, takže se sada oddělovačů může lišit.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez `_l` příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s `_l` příponu jsou shodné s tím rozdílem, že používají předaný v místo toho parametr národního prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
> [!NOTE]
>  Jednotlivé funkce používá statické proměnné místním k analýze řetězec do tokenů. Více vláken tedy můžete volat současně tyto funkce bez nežádoucí účinky. Ale v rámci jedním vláknem, prokládání volání na jednu z těchto funkcí je velmi pravděpodobné vytvořit poškození dat a nepřesné výsledky. Při analýze různé řetězce, dokončete před zahájením analyzovat další analýza jeden řetězec. Také znát potenciální nebezpečí při volání jednu z těchto funkcí z v rámci smyčku, kde je volán jinou funkci. Pokud jiné funkce skončí pomocí jedné z těchto funkcí, bude výsledek prokládaná posloupnost volání, aktivuje poškození dat.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstok`|`strtok`|`_mbstok`|`wcstok`|  
|`_tcstok`|`_strtok_l`|`_mbstok_l`|`_wcstok_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strtok`|\<String.h >|  
|`wcstok`|\<String.h > nebo \<wchar.h >|  
|`_mbstok`, `_mbstok_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strtok.c  
// compile with: /W3  
// In this program, a loop uses strtok  
// to print all the tokens (separated by commas  
// or blanks) in the string named "string".  
//  
#include <string.h>  
#include <stdio.h>  
  
char string[] = "A string\tof ,,tokens\nand some  more tokens";  
char seps[]   = " ,\t\n";  
char *token;  
  
int main( void )  
{  
   printf( "Tokens:\n" );  
  
   // Establish string and get the first token:  
   token = strtok( string, seps ); // C4996  
   // Note: strtok is deprecated; consider using strtok_s instead  
   while( token != NULL )  
   {  
      // While there are tokens in "string"  
      printf( " %s\n", token );  
  
      // Get next token:   
      token = strtok( NULL, seps ); // C4996  
   }  
}  
```  
  
```Output  
Tokens:  
 A  
 string  
 of  
 tokens  
 and  
 some  
 more  
 tokens  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn –, wcscspn –, _mbscspn –, _mbscspn_l –](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)