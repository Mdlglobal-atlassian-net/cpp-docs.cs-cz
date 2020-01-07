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
ms.openlocfilehash: 331d43f3e3a88786f8dac0a6f609f988beea9dbb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300303"
---
# <a name="filename-search-functions"></a>Funkce vyhledávání názvů souborů

Tyto funkce hledají a zavřou hledání u zadaných názvů souborů:

- [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)

- [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)

- [_findclose](../c-runtime-library/reference/findclose.md)

## <a name="remarks"></a>Poznámky

Funkce `_findfirst` poskytuje informace o první instanci názvu souboru, který se shoduje se souborem zadaným v argumentu `filespec`. Můžete použít v `filespec` libovolnou kombinaci zástupných znaků, které podporuje hostitelský operační systém.

Funkce vrací informace o souboru ve `_finddata_t` struktuře, která je definována v IO. h. Různé funkce v rodině využívají mnoho variant `_finddata_t` struktury. Základní struktura `_finddata_t` zahrnuje následující prvky:

`unsigned attrib`<br/>
Atribut File

`time_t time_create`<br/>
Čas vytvoření souboru (-1L pro systémy souborů FAT). Tento čas je uložen ve formátu UTC. Pro převod na místní čas použijte [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).

`time_t time_access`<br/>
Čas posledního přístupu k souboru (-1L pro systémy souborů FAT). Tento čas je uložen ve formátu UTC. Pro převod na místní čas použijte `localtime_s`.

`time_t time_write`<br/>
Čas posledního zápisu do souboru. Tento čas je uložen ve formátu UTC. Pro převod na místní čas použijte `localtime_s`.

`_fsize_t size`<br/>
Délka souboru v bajtech

`char name`[`_MAX_PATH`] název souboru nebo adresáře zakončený hodnotou null, bez cesty.

V systémech souborů, které nepodporují dobu vytváření a posledního přístupu k souboru, jako je například systém souborů FAT, jsou pole `time_create` a `time_access` vždycky-1L.

`_MAX_PATH` je definována v Stdlib. h jako 260 bajtů.

Pro omezení operace Find nelze zadat cílové atributy (například `_A_RDONLY`). Tyto atributy jsou vráceny v poli `attrib` struktury `_finddata_t` a mohou mít následující hodnoty (definované v IO. h). Uživatelé by neměli spoléhat na to, že se jedná o jediné hodnoty možné pro pole `attrib`.

`_A_ARCH`<br/>
Zálohovat. Nastaví se pokaždé, když se soubor změní a vymaže příkazem **Backup** . Hodnota: 0x20.

`_A_HIDDEN`<br/>
Skrytý soubor. Obecně se nezobrazuje v příkazu DIR, pokud nepoužijete možnost **/Ah** . Vrátí informace o běžných souborech a souborech, které mají tento atribut. Hodnota: 0x02.

`_A_NORMAL`<br/>
Běžnou. Soubor nemá žádné další atributy nastavené a lze ho číst nebo zapisovat do bez omezení. Hodnota: 0x00.

`_A_RDONLY`<br/>
Jen pro čtení. Soubor nelze otevřít pro zápis a soubor, který má stejný název, nelze vytvořit. Hodnota: 0x01.

`_A_SUBDIR`<br/>
Podadresář. Hodnota: 0x10.

`_A_SYSTEM`<br/>
Systémový soubor. Nezobrazuje se obvykle pomocí příkazu **dir** , pokud není použita možnost **/a** nebo **/a: S** . Hodnota: 0x04.

`_findnext` najde další název, pokud existuje, který odpovídá argumentu `filespec` určenému ve starším volání `_findfirst`. Argument `fileinfo` by měl ukazovat na strukturu inicializovaná předchozím voláním `_findfirst`. Pokud je nalezena shoda, obsah struktury `fileinfo` se změnil, jak je popsáno výše. V opačném případě zůstane beze změny. `_findclose` zavře zadaný vyhledávací popisovač a uvolní všechny přidružené prostředky pro `_findfirst` i `_findnext`. Popisovač vrácený buď `_findfirst`, nebo `_findnext` musí být nejprve předán do `_findclose`, než operace úprav, jako je například odstranění, lze provést v adresářích, které tvoří cesty, které jsou předány.

Funkce `_find` můžete vnořovat. Například pokud volání `_findfirst` nebo `_findnext` najde soubor, který je podadresářem, je možné zahájit nové hledání s jiným voláním `_findfirst` nebo `_findnext`.

`_wfindfirst` a `_wfindnext` jsou verze systémů `_findfirst` a `_findnext`s velkým počtem znaků. Argument Structure u verzí s velkým znakem má `_wfinddata_t` datový typ, který je definován v IO. h a v WCHAR. h. Pole tohoto datového typu jsou stejná jako u datového typu `_finddata_t`, s tím rozdílem, že v `_wfinddata_t` pole název je typu `wchar_t` místo typu `char`. Jinak `_wfindfirst` a `_wfindnext` se chovají stejně jako `_findfirst` a `_findnext`.

`_findfirst` a `_findnext` použít typ času 64. Pokud je nutné použít starý typ času 32, můžete definovat `_USE_32BIT_TIME_T`. Verze těchto funkcí, které mají příponu `32` v jejich názvech používají typ času 32, a ty s příponou `64` používají typ času 64-bit.

Funkce `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`a `_wfindnext32i64` se také chovají stejně jako verze typu 32 bitového času těchto funkcí s tím rozdílem, že používají a vracejí 64 bitů souborů. Funkce `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`a `_wfindnext64i32` používají typ času 64-bit, ale používají 32 délky souborů. Tyto funkce používají odpovídající variace typu `_finddata_t`, ve kterém mají pole různé typy pro čas a velikost souboru.

`_finddata_t` je ve skutečnosti makro, které se vyhodnocuje jako `_finddata64i32_t` (nebo `_finddata32_t` Pokud je definována `_USE_32BIT_TIME_T`). Následující tabulka shrnuje variace `_finddata_t`:

|Struktura|Typ času|Typ velikosti souboru|
|---------------|---------------|--------------------|
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|

`_fsize_t` je `typedef` pro `unsigned long` (32 bitů).

## <a name="example"></a>Příklad

```c
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
