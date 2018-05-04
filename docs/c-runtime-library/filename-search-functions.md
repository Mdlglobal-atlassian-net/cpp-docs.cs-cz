---
title: Funkce vyhledávání filename | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 777ac61828abbdc93bdf3fe6ceda05f927472494
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="filename-search-functions"></a>Název souboru – funkce hledání
Tyto funkce Hledat a zavřete Vyhledá zadaný soubor názvy:  
  
-   [_findnext –, _wfindnext –](../c-runtime-library/reference/findnext-functions.md)  
  
-   [_findfirst –, _wfindfirst –](../c-runtime-library/reference/findfirst-functions.md)  
  
-   [_findclose](../c-runtime-library/reference/findclose.md)  
  
## <a name="remarks"></a>Poznámky  
 `_findfirst` Funkce poskytuje informace o první instance název souboru, který odpovídá zadané v souboru `filespec` argument. Můžete použít v `filespec` libovolnou kombinaci zástupné znaky, kterou podporuje tento hostitelský operační systém.  
  
 Funkce vrátí informace o souborech v `_finddata_t` struktura, která je definována v IO.h. Různé funkce v dané rodině použít mnoho variant na `_finddata_t` struktura. Základní `_finddata_t` struktura zahrnuje následující prvky:  
  
 `unsigned attrib`  
 Atribut souboru.  
  
 `time_t time_create`  
 Čas vytvoření souboru (-1 L systémů souborů FAT). Tato doba je uložený ve formátu UTC. Chcete-li převést na místní čas, použijte [localtime_s –](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).  
  
 `time_t time_access`  
 Čas poslední přístup k souborům (-1 L systémů souborů FAT). Tato doba je uložený ve formátu UTC. Chcete-li převést na místní čas, použijte `localtime_s`.  
  
 `time_t time_write`  
 Čas poslední zápis do souboru. Tato doba je uložený ve formátu UTC. Chcete-li převést na místní čas, použijte `localtime_s`.  
  
 `_fsize_t size`  
 Délka souboru v bajtech.  
  
 `char name`[ `_MAX_PATH`]  
 Ukončené hodnotou Null název odpovídající soubor nebo adresář bez cesty.  
  
 V systémech souborů, které nepodporují vytváření a času posledního přístupu k souboru, jako je například systém souborů FAT `time_create` a `time_access` pole jsou vždy L-1.  
  
 `_MAX_PATH` je definována v Stdlib.h 260 bajtů.  
  
 Nelze zadat cílový atributy (například `_A_RDONLY`) k omezení operace hledání. Tyto atributy se vrátí `attrib` pole z `_finddata_t` struktury a může mít následující hodnoty (definovaná v IO.h). Uživatelé neměli spoléhat na to je možné pouze tyto hodnoty `attrib` pole.  
  
 `_A_ARCH`  
 Archivu. Nastavit vždy, když je soubor změnit a schválena **zálohování** příkaz. Hodnota: 0x20 vlastnosti.  
  
 `_A_HIDDEN`  
 Skrytého souboru. Chyba není obecně se příkaz DIR, pokud nechcete použít **/AH** možnost. Vrací informace o normální soubory a soubory, které mají tento atribut. Hodnota: 0x02.  
  
 `_A_NORMAL`  
 Normální. Soubor neobsahuje žádné další atributy nastavení a můžou číst nebo zapisovat do bez omezení. Hodnota: 0x00.  
  
 `_A_RDONLY`  
 Jen pro čtení. Soubor nelze otevřít pro zápis a nedá se vytvořit soubor, který má stejný název. Hodnota: 0x01.  
  
 `_A_SUBDIR`  
 Podadresář. Hodnota: 0x10.  
  
 `_A_SYSTEM`  
 Systémový soubor. Chyba se objevuje není normálně **DIR** příkaz, pokud **/A** nebo **/A:S** možnost se používá. Hodnota: 0x04.  
  
 `_findnext` Vyhledá další název, pokud existuje, který odpovídá `filespec` argument zadaná v dřívější volání `_findfirst`. `fileinfo` Argument by měla odkazovat na strukturu inicializuje pomocí volání předchozí `_findfirst`. Pokud je nalezena shoda, `fileinfo` struktura obsah se změnil, jak bylo popsáno výše. Jinak, je ponechán beze změny. `_findclose` zavře popisovač zadaný hledaný a všechny přidružené prostředky pro obě `_findfirst` a `_findnext`. Popisovač vrácený buď `_findfirst` nebo `_findnext` musí být předán nejprve `_findclose`, před provedením operace úpravy, například odstraňování, na adresáře, které tvoří cesty předán do je.  
  
 Lze vnořit `_find` funkce. Například, pokud volání `_findfirst` nebo `_findnext` najde soubor, který je podadresáři, nové hledání lze inicializovat s jiným voláním `_findfirst` nebo `_findnext`.  
  
 `_wfindfirst` a `_wfindnext` jsou verze široká charakterová `_findfirst` a `_findnext`. Struktura argument verze široká charakterová má `_wfinddata_t` datového typu, který je definován v IO.h a Wchar.h. Tento datový typ pole jsou stejné jako `_finddata_t` datového typu, s výjimkou, že v `_wfinddata_t` je pole Název typu `wchar_t` místo typu `char`. V opačném případě `_wfindfirst` a `_wfindnext` chovají stejně jako na `_findfirst` a `_findnext`.  
  
 `_findfirst` a `_findnext` použít typ 64-bit času. Pokud musíte použít typ staré času 32-bit, můžete definovat `_USE_32BIT_TIME_T`. Verze tyto funkce, které mají `32` příponu jejich názvy použít typ 32-bit času a akcemi s `64` příponu použít typ 64-bit času.  
  
 Funkce `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`, a `_wfindnext32i64` také chovaly stejně jako čas 32bitové verze typ tyto funkce s výjimkou používají a vrátí soubor 64-bit délky. Funkce `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`, a `_wfindnext64i32` použít typ času 64-bit, ale použijte 32bitový soubor délky. Tyto funkce použijte příslušné variace `_finddata_t` typ, ve kterém pole mají různé typy pro čas a velikost souboru.  
  
 `_finddata_t` ve skutečnosti makra, jehož výsledkem je `_finddata64i32_t` (nebo `_finddata32_t` Pokud `_USE_32BIT_TIME_T` je definována). Následující tabulka shrnuje variace na `_finddata_t`:  
  
|Struktura|Typ času|Typ velikosti souboru|  
|---------------|---------------|--------------------|  
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|  
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|  
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|  
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|  
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|  
  
 `_fsize_t` je `typedef` pro `unsigned long` (32bitová verze).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_find.c  
// This program uses the 32-bit _find functions to print  
// a list of all files (and their attributes) with a .C extension  
// in the current directory.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _finddata_t c_file;  
   intptr_t hFile;  
  
   // Find first .c file in current directory   
   if( (hFile = _findfirst( "*.c", &c_file )) == -1L )  
      printf( "No *.c files in current directory!\n" );  
   else  
   {  
      printf( "Listing of .c files\n\n" );  
      printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' );  
      printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' );  
      do {  
         char buffer[30];  
         printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " );  
         printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " );  
         ctime_s( buffer, _countof(buffer), &c_file.time_write );  
         printf( " %-12s %.24s  %9ld\n",  
            c_file.name, buffer, c_file.size );  
      } while( _findnext( hFile, &c_file ) == 0 );  
      _findclose( hFile );  
   }  
}  
```  
  
```Output  
Listing of .c files  
  
RDO HID SYS ARC  FILE         DATE                           SIZE  
--- --- --- ---  ----         ----                           ----  
 N   N   N   Y   blah.c       Wed Feb 13 09:21:42 2002       1715  
 N   N   N   Y   test.c       Wed Feb 06 14:30:44 2002        312  
```  
  
## <a name="see-also"></a>Viz také  
 [Systémová volání](../c-runtime-library/system-calls.md)