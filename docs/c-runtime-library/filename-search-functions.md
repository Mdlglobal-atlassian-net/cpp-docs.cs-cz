---
title: Funkce hledání názvů souborů
ms.date: 11/04/2016
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
apitype: DLLExport
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
ms.openlocfilehash: aebdf2e5aaf6d59e5ee39af05540604206ec6c23
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740547"
---
# <a name="filename-search-functions"></a>Funkce hledání názvů souborů

Tyto funkce hledání a zavřete Vyhledá zadaný soubor názvy:

- [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)

- [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)

- [_findclose](../c-runtime-library/reference/findclose.md)

## <a name="remarks"></a>Poznámky

`_findfirst` Funkce obsahuje informace o první výskyt název souboru, který odpovídá zadané v souboru `filespec` argument. Můžete použít v `filespec` libovolnou kombinaci zástupných znaků, která je podporována operačním systémem hostitele.

Funkce vrací informace o souboru v `_finddata_t` struktura, která je definována v IO.h. Různé funkce v rodině použít mnoho variant na `_finddata_t` struktury. Na úrovni basic `_finddata_t` struktura obsahuje následující prvky:

`unsigned attrib`<br/>
Atribut souboru.

`time_t time_create`<br/>
Čas vytvoření souboru (L-1 pro systémy souborů FAT). Tentokrát je uložen ve formátu UTC. Chcete-li převést na místní čas, použijte [localtime_s –](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).

`time_t time_access`<br/>
Čas posledního přístupu k souboru (L-1 pro systémy souborů FAT). Tentokrát je uložen ve formátu UTC. Chcete-li převést na místní čas, použijte `localtime_s`.

`time_t time_write`<br/>
Čas posledního zápisu do souboru. Tentokrát je uložen ve formátu UTC. Chcete-li převést na místní čas, použijte `localtime_s`.

`_fsize_t size`<br/>
Délka souboru v bajtech.

`char name`[ `_MAX_PATH`] Název odpovídající soubor nebo adresář bez cesty zakončený hodnotou null.

V systémech souborů, které nepodporují vytváření a času posledního přístupu k souboru, jako je například systém souborů FAT `time_create` a `time_access` pole jsou vždy hodnotu-1 L.

`_MAX_PATH` je definována v souboru Stdlib.h jako 260 bajtů.

Nelze určit cílové atributy (například `_A_RDONLY`) k omezení operace find. Tyto atributy jsou vráceny v `attrib` pole `_finddata_t` struktury a může mít následující hodnoty (definovaný v IO.h). Uživatelé neměli byste tedy spoléhat na tyto jsou pouze hodnoty, který je možné, `attrib` pole.

`_A_ARCH`<br/>
Archivovat. Nastavit vždy, když je soubor změněn a zrušena **zálohování** příkazu. Hodnota: 0x20.

`_A_HIDDEN`<br/>
Skrytý soubor. Pomocí příkazu DIR viděli obecně, pokud nechcete použít **/AH** možnost. Vrátí informace o normální soubory a soubory, které mají tento atribut. Hodnota: 0x02.

`_A_NORMAL`<br/>
Normální. Soubor nemá žádné další atributy nastavit a může číst nebo zapsat bez omezení. Hodnota: 0x00.

`_A_RDONLY`<br/>
Jen pro čtení. Soubor nelze otevřít pro zápis a nelze vytvořit soubor, který má stejný název. Hodnota: 0x01.

`_A_SUBDIR`<br/>
Podadresář. Hodnota: 0x10.

`_A_SYSTEM`<br/>
Systém souborů. Není obvykle používá u **DIR** příkazu, pokud **/A** nebo **/A:S** možnost se používá. Hodnota: 0x04.

`_findnext` Najde další název, pokud existuje, který odpovídá `filespec` argumentu zadaného v dřívějším volání `_findfirst`. `fileinfo` Argument by měl ukazovat na strukturu inicializován pomocí předchozího volání `_findfirst`. Pokud se najde shoda, `fileinfo` se změnil obsah struktury, jak je popsáno výše. V opačném případě je ponechán beze změny. `_findclose` zadaný hledaný popisovač se zavře a uvolní všechny související prostředky pro obě `_findfirst` a `_findnext`. Popisovač vrácený buď `_findfirst` nebo `_findnext` musí být předán nejprve `_findclose`, před provedením operace úprav, jako je například odstranění, o adresářích, které tvoří cesty předaný k nim.

Můžete vnořit `_find` funkce. Například, pokud je volání `_findfirst` nebo `_findnext` najde soubor, který je podadresář, nové hledání lze inicializovat pomocí jiného volání `_findfirst` nebo `_findnext`.

`_wfindfirst` a `_wfindnext` jsou širokoznaké verze `_findfirst` a `_findnext`. Struktura argument širokoznaké verze má `_wfinddata_t` datový typ, který je definován v IO.h a v souboru Wchar.h. Pole datového typu jsou stejné jako `_finddata_t` datového typu, s výjimkou, že v `_wfinddata_t` název pole je typu `wchar_t` místo typu `char`. V opačném případě `_wfindfirst` a `_wfindnext` chovají stejně jako `_findfirst` a `_findnext`.

`_findfirst` a `_findnext` použít 64-bit time typu. Pokud je nutné použít typ staré 32bitové času, můžete definovat `_USE_32BIT_TIME_T`. Verze těchto funkcí, které mají `32` přípony v názvu použijte typ času 32-bit a těmi, kdo `64` příponu použít 64-bit time typu.

Funkce `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`, a `_wfindnext32i64` také se chovají stejně jako čas 32bitové verze typů z těchto funkcí s výjimkou použití a vrácení délky souboru 64-bit. Funkce `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`, a `_wfindnext64i32` použít 64-bit time typu, ale použijte 32bitový soubor délky. Tyto funkce používají odpovídající variace `_finddata_t` typ, ve kterém pole mají rozdílné typy pro čas a velikost souboru.

`_finddata_t` je ve skutečnosti makro, které se vyhodnotí jako `_finddata64i32_t` (nebo `_finddata32_t` Pokud `_USE_32BIT_TIME_T` je definována). Následující tabulka shrnuje změny na `_finddata_t`:

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

## <a name="see-also"></a>Viz také:

[Systémová volání](../c-runtime-library/system-calls.md)
