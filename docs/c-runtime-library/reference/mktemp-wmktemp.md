---
title: "_mktemp –, _wmktemp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wmktemp
- _mktemp
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
dev_langs: C++
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ade54aef0413e6db897b00f7bfa2e78c428366a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp
Vytvoří jedinečný název souboru. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_mktemp_s –, _wmktemp_s –](../../c-runtime-library/reference/mktemp-s-wmktemp-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_mktemp(  
   char *template   
);  
wchar_t *_wmktemp(  
   wchar_t *template   
);  
template <size_t size>  
char *_mktemp(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wmktemp(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `template`  
 Vzor názvů souborů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací ukazatel na šabloně upravené. Funkce vrátí hodnotu `NULL` Pokud `template` je chybně vytvořen nebo je možné vytvářet žádné další jedinečné názvy z dané šablony.  
  
## <a name="remarks"></a>Poznámky  
 `_mktemp` Funkce vytvoří jedinečný název souboru změnou `template` argument. `_mktemp`automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používána v běhu systému. `_wmktemp`široká charakterová verze `_mktemp`; argument a vrátí hodnotu `_wmktemp` jsou široká charakterová řetězce. `_wmktemp`a `_mktemp` chovat jinak, stejně jako vyjma toho, že `_wmktemp` nezpracovává řetězců vícebajtových znaků.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp`|`_mktemp`|`_mktemp`|`_wmktemp`|  
  
 `template` Argument má formulář `base` *XXXXXX*, kde `base` je součástí nový název souboru, který zadáte a každá X je zástupný symbol pro znak poskytl `_mktemp`. Každý zástupný znak v `template` musí být velká X. `_mktemp` zachovává `base` a nahradí první Koncové X znakem abecedy. `_mktemp`nahrazuje následující koncové značkou s hodnotou pět číslic; Tato hodnota je jedinečné číslo identifikující volání zpracovat, nebo programy s více vlákny, volající vlákno.  
  
 Každé úspěšné volání `_mktemp` upraví `template`. Při každém následných volání z stejný postup nebo vlákno se stejným `template` argument, `_mktemp` kontroly pro názvy souborů, které odpovídají názvy vrácené `_mktemp` v předchozích volání. Pokud pro daného názvu, neexistuje žádný soubor `_mktemp` vrátí tímto názvem. Pokud soubory existují pro všechny názvy, předtím vrátila `_mktemp` vytvoří nový název nahrazením znak abecedy použije v názvu dříve vrácený s další dostupné malé písmeno, v pořadí od 'a' do 'z'. Například pokud `base` je:  
  
```  
fn  
```  
  
 a hodnotu pět číslic poskytl `_mktemp` 12345, je vrácena křestní jméno:  
  
```  
fna12345  
```  
  
 Pokud tento název se používá k vytvoření souboru FNA12345 a tento soubor stále existuje, další název vrátila volání ze stejné procesu nebo vlákno se stejným `base` pro `template` je:  
  
```  
fnb12345  
```  
  
 Pokud FNA12345 neexistuje, je další název vrácený znovu:  
  
```  
fna12345  
```  
  
 `_mktemp`můžete vytvořit maximálně 26 jedinečných názvů souborů pro libovolnou kombinaci dané hodnoty základní a šablony. Proto je FNZ12345 příjmení jedinečný soubor `_mktemp` můžete vytvořit pro `base` a `template` hodnoty používané v tomto příkladu.  
  
 Při selhání `errno` nastavena. Pokud `template` má neplatný formát (například méně než 6 značkou), `errno` je nastaven na `EINVAL`. Pokud `_mktemp` se nepodařilo vytvořit jedinečný název, protože názvy všech 26 možné soubor již existuje, `_mktemp` nastaví šablonu na prázdný řetězec a vrátí `EEXIST`.  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mktemp`|\<IO.h >|  
|`_wmktemp`|\<IO.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_mktemp.c  
// compile with: /W3  
/* The program uses _mktemp to create  
 * unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
#include <errno.h>  
  
char *template = "fnXXXXXX";  
char *result;  
char names[27][9];  
  
int main( void )  
{  
   int i;  
   FILE *fp;  
  
   for( i = 0; i < 27; i++ )  
   {  
      strcpy_s( names[i], sizeof( names[i] ), template );  
      /* Attempt to find a unique filename: */  
      result = _mktemp( names[i] );  // C4996  
      // Note: _mktemp is deprecated; consider using _mktemp_s instead  
      if( result == NULL )  
      {  
         printf( "Problem creating the template\n" );  
         if (errno == EINVAL)  
         {  
             printf( "Bad parameter\n");  
         }  
         else if (errno == EEXIST)  
         {  
             printf( "Out of unique filenames\n");   
         }  
      }  
      else  
      {  
         fopen_s( &fp, result, "w" );  
         if( fp != NULL )  
            printf( "Unique filename is %s\n", result );  
         else  
            printf( "Cannot open %s\n", result );  
         fclose( fp );  
      }  
   }  
}  
```  
  
```Output  
Unique filename is fna03912  
Unique filename is fnb03912  
Unique filename is fnc03912  
Unique filename is fnd03912  
Unique filename is fne03912  
Unique filename is fnf03912  
Unique filename is fng03912  
Unique filename is fnh03912  
Unique filename is fni03912  
Unique filename is fnj03912  
Unique filename is fnk03912  
Unique filename is fnl03912  
Unique filename is fnm03912  
Unique filename is fnn03912  
Unique filename is fno03912  
Unique filename is fnp03912  
Unique filename is fnq03912  
Unique filename is fnr03912  
Unique filename is fns03912  
Unique filename is fnt03912  
Unique filename is fnu03912  
Unique filename is fnv03912  
Unique filename is fnw03912  
Unique filename is fnx03912  
Unique filename is fny03912  
Unique filename is fnz03912  
Problem creating the template.  
Out of unique filenames.  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp –](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid –](../../c-runtime-library/reference/getpid.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp –](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam –, _wtempnam –, tmpnam –, _wtmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile –](../../c-runtime-library/reference/tmpfile.md)