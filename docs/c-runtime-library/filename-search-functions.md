---
title: Funkce vyhledávání názvů souborů
ms.date: 11/04/2016
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
ms.openlocfilehash: ecc01362bdc14af32df5093ad1ac1ee606026d8f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940369"
---
# <a name="filename-search-functions"></a>Funkce vyhledávání názvů souborů

Tyto funkce hledají a zavřou hledání u zadaných názvů souborů:

- [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)

- [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)

- [_findclose](../c-runtime-library/reference/findclose.md)

## <a name="remarks"></a>Poznámky

Funkce poskytuje informace o první instanci názvu souboru, který se shoduje se souborem zadaným `filespec` v argumentu. `_findfirst` Můžete použít v `filespec` libovolné kombinaci zástupných znaků, které podporuje hostitelský operační systém.

Funkce vrací informace o souboru ve `_finddata_t` struktuře, která je definována v IO. h. Různé funkce v rodině využívají mnoho variant `_finddata_t` struktury. Základní `_finddata_t` struktura zahrnuje následující prvky:

`unsigned attrib`<br/>
Atribut File

`time_t time_create`<br/>
Čas vytvoření souboru (-1L pro systémy souborů FAT). Tento čas je uložen ve formátu UTC. Chcete-li převod na místní čas, použijte [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).

`time_t time_access`<br/>
Čas posledního přístupu k souboru (-1L pro systémy souborů FAT). Tento čas je uložen ve formátu UTC. Pro převod na místní čas použijte `localtime_s`.

`time_t time_write`<br/>
Čas posledního zápisu do souboru. Tento čas je uložen ve formátu UTC. Pro převod na místní čas použijte `localtime_s`.

`_fsize_t size`<br/>
Délka souboru v bajtech

`char name`[ `_MAX_PATH`] Název souboru nebo adresáře zakončený hodnotou null, bez cesty.

V systémech souborů, které nepodporují dobu vytváření a posledního přístupu k souboru, jako je například systém souborů FAT, `time_create` jsou pole a `time_access` vždy-1l.

`_MAX_PATH`je definována v Stdlib. h jako 260 bajtů.

Pro omezení operace Find nelze zadat cílové atributy `_A_RDONLY`(například). Tyto atributy jsou vráceny v `attrib` poli `_finddata_t` struktury a mohou mít následující hodnoty (definované v IO. h). Uživatelé by neměli spoléhat na to, že jsou pro `attrib` pole dostupné jenom hodnoty.

`_A_ARCH`<br/>
Zálohovat. Nastaví se pokaždé, když se soubor změní a vymaže příkazem **Backup** . Osa 0x20.

`_A_HIDDEN`<br/>
Skrytý soubor. Obecně se nezobrazuje v příkazu DIR, pokud nepoužijete možnost **/Ah** . Vrátí informace o běžných souborech a souborech, které mají tento atribut. Osa 0x02.

`_A_NORMAL`<br/>
Běžnou. Soubor nemá žádné další atributy nastavené a lze ho číst nebo zapisovat do bez omezení. Osa 0x00.

`_A_RDONLY`<br/>
Jen pro čtení. Soubor nelze otevřít pro zápis a soubor, který má stejný název, nelze vytvořit. Osa 0x01.

`_A_SUBDIR`<br/>
Podadresář. Osa 0x10.

`_A_SYSTEM`<br/>
Systémový soubor. Nezobrazuje se obvykle pomocí příkazu **dir** , pokud není použita možnost **/a** nebo **/a: S** . Osa 0x04.

`_findnext`najde další název, pokud existuje, který odpovídá `filespec` argumentu zadanému ve starším `_findfirst`volání metody. Argument by měl ukazovat na strukturu inicializovaná předchozím `_findfirst`voláním metody. `fileinfo` Pokud je nalezena shoda, `fileinfo` obsah struktury se změní jak je popsáno výše. V opačném případě zůstane beze změny. `_findclose`zavře zadaný vyhledávací popisovač a uvolní všechny přidružené prostředky pro i `_findfirst`. `_findnext` Popisovač vrácený buď `_findfirst` nebo `_findnext` musí být nejprve předán do `_findclose`, před provedením operací úprav, jako je například odstranění, lze provést v adresářích, které tvoří cesty, které jsou předány.

`_find` Funkce lze vnořit. Například pokud volání `_findfirst` nebo `_findnext` nalezne soubor, který je podadresářem, lze nové hledání `_findfirst` zahájit jiným voláním nebo `_findnext`.

`_wfindfirst`a `_wfindnext` jsou `_findfirst` verze a `_findnext`. Argument Structure verze s vysokými znaky má `_wfinddata_t` datový typ, který je definován v IO. h a v WCHAR. h. Pole tohoto datového typu jsou stejná `_finddata_t` jako u datového typu, s tím rozdílem, že v `_wfinddata_t` poli název je typ `wchar_t` místo typu `char`. V opačném případě `_wfindfirst` se `_findfirst` `_findnext`chovástejnějakoa. `_wfindnext`

`_findfirst`a `_findnext` použijte typ času 64. Pokud je nutné použít starý typ času 32, můžete definovat `_USE_32BIT_TIME_T`. Verze těchto funkcí, které mají `32` příponu ve svých názvech, používají typ času 32, a ty `64` s příponou používají typ času 64.

Funkce `_findfirst32i64`, `_findnext32i64`, a`_wfindfirst32i64`se také chovají stejně jako verze s 32 bitového formátu času těchto funkcí s tím rozdílem, že používají a vracejí 64 bitů souborů. `_wfindnext32i64` Funkce `_findfirst64i32` ,`_findnext64i32`, a`_wfindnext64i32` používají typ času 64-bit, ale používají 32 délky souborů. `_wfindfirst64i32` Tyto funkce používají odpovídající variace `_finddata_t` typu, ve kterém mají pole různé typy pro čas a velikost souboru.

`_finddata_t`je ve skutečnosti makro, které se vyhodnotí `_finddata32_t` jako `_USE_32BIT_TIME_T` `_finddata64i32_t` (nebo pokud je definováno). Následující tabulka shrnuje variace pro `_finddata_t`:

|Struktura|Typ času|Typ velikosti souboru|
|---------------|---------------|--------------------|
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|

`_fsize_t`je a `typedef` pro `unsigned long` (32 bitů).

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

## <a name="see-also"></a>Viz také:

[Systémová volání](../c-runtime-library/system-calls.md)
