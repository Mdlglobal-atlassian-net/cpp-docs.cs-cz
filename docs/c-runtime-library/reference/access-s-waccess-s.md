---
title: _access_s, _waccess_s
ms.date: 11/04/2016
apiname:
- _access_s
- _waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: 17d19527323f3e97edecd22ca7c0a0262b1cfbad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541515"
---
# <a name="accesss-waccesss"></a>_access_s, _waccess_s

Určuje oprávnění ke čtení a zápis souborů. Toto je verze [_přístupový _waccess –](access-waccess.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parametry

*Cesta*<br/>
Cesta k souboru nebo adresáře.

*Režim*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí hodnotu 0, pokud má soubor dané režimu. Funkce vrátí kód chyby, pokud pojmenovaný soubor neexistuje nebo není přístupný v daném režimu. V takovém případě funkce vrátí kód chyby ze sady následujícím způsobem a také nastaví `errno` na stejnou hodnotu.

|Hodnota errno|Podmínka|
|-|-|
`EACCES`|Přístup byl odepřen. Nastavení oprávnění k souboru neumožňuje zadaný přístup.
`ENOENT`|Název souboru nebo cesta nebyla nalezena.
`EINVAL`|Neplatný parametr.

Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Při použití s soubory, **_access_s –** funkce určuje, zda zadaný soubor existuje a je přístupná jako zadaný hodnotou *režimu*. Při použití s adresáři, **_access_s –** pouze určuje, zda existuje zadaný adresář. Všechny adresáře v systému Windows 2000 a novějších operačních systémech, čtení a zápisu přístup.

|Hodnota režimu|Soubor kontroly|
|----------------|---------------------|
|00|Pouze existence.|
|02|Oprávnění k zápisu.|
|04|Oprávnění ke čtení.|
|06|Oprávnění ke čtení a zápisu.|

Oprávnění ke čtení nebo zápisu souboru není dostatečně zajistit možnost otevření souboru. Například pokud je soubor uzamčen jiným procesem, nemusí být dostupné i v případě **_access_s –** vrátí hodnotu 0.

**_waccess_s –** je verze širokého znaku **_access_s –**, kde *cesta* argument **_waccess_s –** je širokoznaký řetězec. V opačném případě **_waccess_s –** a **_access_s –** chovají identicky.

Tyto funkce ověřují své parametry. Pokud *cesta* má hodnotu NULL nebo *režimu* neurčuje platný režim, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví `errno` k `EINVAL` a vrátit `EINVAL`.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_access_s**|\<IO.h >|\<errno.h>|
|**_waccess_s**|\<wchar.h > nebo \<io.h >|\<errno.h>|

## <a name="example"></a>Příklad

Tento příklad používá **_access_s –** zkontrolovat soubor s názvem crt_access_s.c zobrazíte, zda existuje a zda je povolen zápis.

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat – funkce](stat-functions.md)