---
title: "_mktemp_s –, _wmktemp_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mktemp_s
- _wmktemp_s
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
apitype: DLLExport
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs: C++
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d87ba7e23ccc50cb6debbdb91912f1ae3e90ce1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mktemps-wmktemps"></a>_mktemp_s, _wmktemp_s
Vytvoří jedinečný název souboru. Toto jsou verze [_mktemp –, _wmktemp –](../../c-runtime-library/reference/mktemp-wmktemp.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _mktemp_s(  
   char *template,  
   size_t sizeInChars  
);  
errno_t _wmktemp_s(  
   wchar_t *template,  
   size_t sizeInChars  
);  
template <size_t size>  
errno_t _mktemp_s(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
errno_t _wmktemp_s(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `template`  
 Vzor názvů souborů.  
  
 `sizeInChars`  
 Velikost vyrovnávací paměti v jednobajtové znaky v `_mktemp_s`; široké znaky v `_wmktemp_s`, včetně ukončení hodnotu null.  
  
## <a name="return-value"></a>Návratová hodnota  
 Obě tyto funkce vrátí nula v případě úspěchu; Kód chyby při selhání.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`template`|`sizeInChars`|**Návratová hodnota**|**Nová hodnota v šabloně**|  
|----------------|-------------------|----------------------|-------------------------------|  
|`NULL`|všechny|`EINVAL`|`NULL`|  
|Nesprávný formát (viz `Remarks` části správný formát)|všechny|`EINVAL`|prázdný řetězec.|  
|všechny|< = počet značkou|`EINVAL`|prázdný řetězec.|  
  
 Pokud dojde k některé z výše uvedených podmínek chyba, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a vrátí funkce `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_mktemp_s` Funkce vytvoří jedinečný název souboru změnou `template` argument, tak, aby po volání `template` ukazatel odkazuje na řetězec obsahující nový název souboru. `_mktemp_s`automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používána v běhu systému. `_wmktemp_s`široká charakterová verze `_mktemp_s`; argument `_wmktemp_s` je široká charakterová řetězec. `_wmktemp_s`a `_mktemp_s` chovat jinak, stejně jako vyjma toho, že `_wmktemp_s` nezpracovává řetězců vícebajtových znaků.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp_s`|`_mktemp_s`|`_mktemp_s`|`_wmktemp_s`|  
  
 `template` Argument má formulář `baseXXXXXX`, kde `base` je součástí nový název souboru, který zadáte a každá X je zástupný symbol pro znak poskytl `_mktemp_s`. Každý zástupný znak v `template` musí být velká X. `_mktemp_s` zachovává `base` a nahradí první Koncové X znakem abecedy. `_mktemp_s`nahrazuje následující koncové značkou s hodnotou pět číslic; Tato hodnota je jedinečné číslo identifikující volání zpracovat, nebo programy s více vlákny, volající vlákno.  
  
 Každé úspěšné volání `_mktemp_s` upraví `template`. Při každém následných volání z stejný postup nebo vlákno se stejným `template` argument, `_mktemp_s` kontroly pro názvy souborů, které odpovídají názvy vrácené `_mktemp_s` v předchozích volání. Pokud pro daného názvu, neexistuje žádný soubor `_mktemp_s` vrátí tímto názvem. Pokud soubory existují pro všechny názvy, předtím vrátila `_mktemp_s` vytvoří nový název nahrazením znak abecedy použije v názvu dříve vrácený s další dostupné malé písmeno, v pořadí od 'a' do 'z'. Například pokud `base` je:  
  
```  
fn  
```  
  
 a hodnotu pět číslic poskytl `_mktemp_s` 12345, je vrácena křestní jméno:  
  
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
  
 `_mktemp_s`můžete vytvořit maximálně 26 jedinečných názvů souborů pro libovolnou kombinaci dané hodnoty základní a šablony. Proto je FNZ12345 příjmení jedinečný soubor `_mktemp_s` můžete vytvořit pro `base` a `template` hodnoty používané v tomto příkladu.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mktemp_s`|\<IO.h >|  
|`_wmktemp_s`|\<IO.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_mktemp_s.cpp  
/* The program uses _mktemp to create  
 * five unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
  
char *fnTemplate = "fnXXXXXX";  
char names[5][9];  
  
int main()  
{  
   int i, err, sizeInChars;  
   FILE *fp;  
  
   for( i = 0; i < 5; i++ )  
   {  
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );  
      /* Get the size of the string and add one for the null terminator.*/  
      sizeInChars = strnlen(names[i], 9) + 1;  
      /* Attempt to find a unique filename: */  
      err = _mktemp_s( names[i], sizeInChars );  
      if( err != 0 )  
         printf( "Problem creating the template" );  
      else  
      {  
         if( fopen_s( &fp, names[i], "w" ) == 0 )  
            printf( "Unique filename is %s\n", names[i] );  
         else  
            printf( "Cannot open %s\n", names[i] );  
         fclose( fp );  
      }  
   }  
  
   return 0;  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
Unique filename is fna03188  
Unique filename is fnb03188  
Unique filename is fnc03188  
Unique filename is fnd03188  
Unique filename is fne03188  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp –](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid –](../../c-runtime-library/reference/getpid.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp –](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam –, _wtempnam –, tmpnam –, _wtmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile_s –](../../c-runtime-library/reference/tmpfile-s.md)