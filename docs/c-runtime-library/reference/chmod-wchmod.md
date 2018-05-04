---
title: _chmod –, _wchmod – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4944f871195b276189014ed9d5d294b9b445fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="chmod-wchmod"></a>_chmod, _wchmod

Změní nastavení oprávnění souborů.

## <a name="syntax"></a>Syntaxe

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název existující soubor.

*pmode*<br/>
Nastavení oprávnění u souboru.

## <a name="return-value"></a>Návratová hodnota

Tyto funkce vrátí 0, pokud se úspěšně změnil nastavení oprávnění. Vrácená hodnota -1 označuje selhání. Pokud zadaný soubor nebyl nalezen, **errno** je nastaven na **enoent –**; Pokud je parametr platný **errno** je nastaven na **einval –**.

## <a name="remarks"></a>Poznámky

**_Chmod –** funkce změní nastavení oprávnění souboru určeného *filename*. Nastavení oprávnění ovládací prvky pro čtení a zápis do souboru. Celočíselný výraz *pmode* obsahuje jedno nebo obě následující manifestu konstanty definované v SYS\Stat.h.

|*pmode*|Význam|
|-|-|
**_S_IREAD –**|Pouze čtení povolené.
**_S_IWRITE –**|Zápis povolen. (Ve skutečnosti povoluje čtení a zápis.)
**_S_IREAD –** &AMP;#124; **_S_IWRITE –**|Čtení a zápis povolen.

Pokud jsou zadány oba konstanty, jsou spojeny s bitové hodnotě or – operátor (**|**). Není-li oprávnění k zápisu, soubor je jen pro čtení. Upozorňujeme, že všechny soubory jsou vždy čitelný; není možné udělit oprávnění jen pro zápis. Proto režimů **_s_iwrite –** a **_s_iread –** | **_s_iwrite –** odpovídají.

**_wchmod –** je verze široká charakterová **_chmod –**; *filename* argument **_wchmod –** je široká charakterová řetězec. **_wchmod –** a **_chmod –** chovat jinak shodně.

Tato funkce ověří jeho parametry. Pokud *pmode* není kombinace jednoho z manifestu konstanty nebo zahrnuje alternativní sady konstant, funkce jednoduše přeskočí ty. Pokud *filename* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu -1.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod –**|**_chmod –**|**_wchmod**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_chmod –**|\<IO.h >|\<SYS/Types.h >, \<sys/stat.h >, \<errno.h >|
|**_wchmod**|\<IO.h > nebo \<wchar.h >|\<SYS/Types.h >, \<sys/stat.h >, \<errno.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
[_stat, _wstat – funkce](stat-functions.md)<br/>
