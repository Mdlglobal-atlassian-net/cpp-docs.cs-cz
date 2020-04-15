---
title: _chmod, _wchmod
ms.date: 4/2/2020
api_name:
- _chmod
- _wchmod
- _o__chmod
- _o__wchmod
api_location:
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: faceb49c921162da042f863abbebbe2ef0a52153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350087"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

Změní nastavení oprávnění k souboru.

## <a name="syntax"></a>Syntaxe

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parametry

*Název_souboru*<br/>
Název existujícího souboru.

*pmode*<br/>
Nastavení oprávnění pro soubor.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí 0, pokud je nastavení oprávnění úspěšně změněno. Vrácená hodnota -1 označuje selhání. Pokud zadaný soubor nebyl nalezen, **je chybné číslo** nastaveno na **ENOENT**; Pokud je parametr neplatný, je **errno** nastaveno na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_chmod** změní nastavení oprávnění souboru určeného *názvem souboru*. Nastavení oprávnění řídí přístup pro čtení a zápis do souboru. Režim celého *čísla* obsahuje jednu nebo obě následující konstanty manifestu definované v souboru SYS\Stat.h.

| *pmode* | Význam |
|-|-|
| **\_S\_IREAD** | Čtení je povoleno pouze. |
| **\_S\_IWRITE** | Psaní povoleno. (Ve skutečnosti umožňuje čtení a zápis.) |
| **\_S\_IREAD** &#124; ** \_\_S IWRITE** | Čtení a psaní povoleno. |

Pokud jsou obě konstanty uvedeny, jsou spojeny**\|** s bitovým nebo operátorem ( ). Pokud není uděleno oprávnění k zápisu, soubor je jen pro čtení. Všimněte si, že všechny soubory jsou vždy čitelné; není možné udělit oprávnění pouze pro zápis. Režimy **_S_IWRITE** a **_S_IREAD** \| **_S_IWRITE** jsou tedy rovnocenné.

**_wchmod** je širokoznaková verze **_chmod**; argument *název souboru,* který **má _wchmod,** je řetězec s širokým znakem. **_wchmod** a **_chmod** se chovají stejně jinak.

Tato funkce ověřuje její parametry. Pokud *pmode* není kombinací jedné z konstant manifestu nebo obsahuje alternativní sadu konstant, funkce je jednoduše ignoruje. Pokud je *název souboru* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí -1.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>, \<sys/stat.h \<>, errno.h>|
|**_wchmod**|\<io.h> \<nebo wchar.h>|\<sys/types.h>, \<sys/stat.h \<>, errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.
```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat funkce](stat-functions.md)<br/>
