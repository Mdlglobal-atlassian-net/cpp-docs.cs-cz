---
title: _chmod, _wchmod
ms.date: 11/04/2016
apiname:
- _chmod
- _wchmod
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 7f3133aac1548be5cb497fe32ae4f9f1c0e238d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595127"
---
# <a name="chmod-wchmod"></a>_chmod, _wchmod

Změní nastavení souboru oprávnění.

## <a name="syntax"></a>Syntaxe

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název existujícího souboru.

*pmode*<br/>
Nastavení oprávnění k souboru.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí 0, pokud na nastavení oprávnění se úspěšně změnil. Návratová hodnota-1 označuje chybu. Pokud zadaný soubor nebyl nalezen, **errno** je nastavena na **ENOENT**; Pokud parametr není platný, **errno** je nastavena na **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Chmod –** funkce změní nastavení oprávnění souboru určeném *filename*. Nastavení oprávnění řídit čtení a zápis do souboru. Celočíselný výraz *pmode* obsahuje jednu nebo obě z následujících konstant manifestu definovaných v SYS\Stat.h.

|*pmode*|Význam|
|-|-|
**_S_IREAD**|Povoleno jen čtení.
**_S_IWRITE**|Zápis povolen. (V podstatě povoluje čtení a zápis.)
**_S_IREAD** &AMP;#124; **_S_IWRITE**|Čtení a zápis povolen.

Když jsou uvedeny oba konstanty, jsou spojeny s bitový operátor or (**|**). Pokud tento parametr není zadaný oprávnění k zápisu, soubor je jen pro čtení. Všimněte si, že všechny soubory budou vždy číst; není možné poskytnout oprávnění jen pro zápis. Proto režimy **_S_IWRITE** a **_S_IREAD** | **_S_IWRITE** jsou ekvivalentní.

**_wchmod –** je verze širokého znaku **_chmod –**; *filename* argument **_wchmod –** je širokoznaký řetězec. **_wchmod –** a **_chmod –** se jinak chovají stejně.

Tato funkce ověřuje své parametry. Pokud *pmode* není kombinaci některou z konstant manifestu nebo zahrnuje alternativní sadu konstant, funkce jednoduše ignoruje ty. Pokud *filename* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí hodnotu -1.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod –**|**_chmod –**|**_wchmod**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_chmod –**|\<IO.h >|\<SYS/Types.h >, \<sys/stat.h >, \<errno.h >|
|**_wchmod**|\<IO.h > nebo \<wchar.h >|\<SYS/Types.h >, \<sys/stat.h >, \<errno.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat – funkce](stat-functions.md)<br/>
