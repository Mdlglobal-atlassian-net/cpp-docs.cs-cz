---
title: _getcwd, _wgetcwd
ms.date: 11/04/2016
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: 4c533f0e716cb9a13c152b9be3c46f60291118d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331789"
---
# <a name="getcwd-wgetcwd"></a>_getcwd, _wgetcwd

Získá aktuální pracovní adresář.

## <a name="syntax"></a>Syntaxe

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro danou cestu.

*maxlen*<br/>
Maximální délka cesty ve znacích: **char** pro **_getcwd** a **wchar_t** pro **_wgetcwd –**.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na *vyrovnávací paměti*. A **NULL** vrátit hodnota označuje chybu, a **errno** je nastaven buď na **ENOMEM**, označující, že není dostatek paměti k přidělení *maxlen* bajtů (když **NULL** argument je zadána jako *vyrovnávací paměti*), nebo **ERANGE**, označující, že cesta je delší než *maxlen*  znaků. Pokud *maxlen* je menší než nebo rovna hodnotě nula, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getcwd** funkce získá celou cestu aktuálního pracovního adresáře na výchozí jednotce a ukládá ji do *vyrovnávací paměti*. Argument typu celé číslo *maxlen* určuje maximální délku cesty. Pokud délka cesty (včetně ukončujícího znaku null) překročí, dojde k chybě *maxlen*. *Vyrovnávací paměti* argument může být **NULL**; vyrovnávací paměť o velikosti alespoň *maxlen* (více pouze v případě potřeby) automaticky přiřazen, pomocí **malloc**, pro uložení této cesty. Tuto vyrovnávací paměť může být později uvolněna voláním **bezplatné** a předají se jí **_getcwd** návratovou hodnotu (ukazatel do přidělené vyrovnávací paměti).

**_getcwd** vrátí řetězec, který představuje cestu aktuálního pracovního adresáře. Pokud je aktuální pracovní adresář nastaven na kořen, řetězec končí zpětným lomítkem ( **\\** ). Pokud je aktuální pracovní adresář nastaven na jiný adresář než kořenový, řetězec končí názvem adresáře, nikoli zpětným lomítkem.

**_wgetcwd –** je verze širokého znaku **_getcwd**; *vyrovnávací paměti* argument a návratová hodnota funkce **_wgetcwd –** jsou širokoznaké řetězce. **_wgetcwd –** a **_getcwd** se jinak chovají stejně.

Když **_DEBUG** a **_CRTDBG_MAP_ALLOC** jsou definovány, volání **_getcwd** a **_wgetcwd –** jsou nahrazena voláními funkcí **_ getcwd_dbg –** a **_wgetcwd_dbg** umožňuje ladit přidělování paměti. Další informace najdete v tématu [_getcwd_dbg _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<Direct.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
