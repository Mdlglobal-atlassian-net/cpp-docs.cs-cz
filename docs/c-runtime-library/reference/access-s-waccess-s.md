---
title: _access_s, _waccess_s
ms.date: 4/2/2020
api_name:
- _access_s
- _waccess_s
- _o__access_s
- _o__waccess_s
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
ms.openlocfilehash: 7f16951b99eb29bcb8c39499c29be1018cb86616
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349129"
---
# <a name="_access_s-_waccess_s"></a>_access_s, _waccess_s

Určuje oprávnění ke čtení a zápisu souborů. Toto je verze [_access, _waccess](access-waccess.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Cestu*<br/>
Cesta k souboru nebo adresáři.

*Režimu*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí hodnotu 0, pokud má soubor daný režim. Funkce vrátí kód chyby, pokud pojmenovaný soubor neexistuje nebo není přístupný v daném režimu. V tomto případě funkce vrátí kód chyby ze sady `errno` takto a také nastaví na stejnou hodnotu.

|hodnota errno|Podmínka|
|-|-|
`EACCES`|Přístup se odepřel. Nastavení oprávnění souboru neumožňuje určený přístup.
`ENOENT`|Název souboru nebo cesta nebyla nalezena.
`EINVAL`|Neplatný parametr.

Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Při použití se soubory **_access_s** funkce určuje, zda zadaný soubor existuje a lze k němu získat přístup podle hodnoty *režimu*. Při použití s adresáři **_access_s** určuje pouze, zda zadaný adresář existuje. V operačních systémech Windows 2000 a novějších mají všechny adresáře přístup pro čtení a zápis.

|hodnota režimu|Zkontroluje, zda soubor obsahuje|
|----------------|---------------------|
|00|Pouze existence.|
|02|Napište oprávnění.|
|04|Přečtěte si oprávnění.|
|06|Přečtěte si a zapište oprávnění.|

Oprávnění ke čtení nebo zápisu souboru nestačí k zajištění možnosti otevřít soubor. Například pokud je soubor uzamčen jiným procesem, nemusí být přístupný i v případě, **že _access_s** vrátí 0.

**_waccess_s** je verze **_access_s**s širokými znaky , kde argument *cesty* k **_waccess_s** je řetězec s širokým znakem. V opačném případě **se _waccess_s** a **_access_s** chovat stejně.

Tyto funkce ověřují jejich parametry. Pokud je *cesta* NULL nebo *režim* neurčuje platný režim, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, `errno` `EINVAL` tyto `EINVAL`funkce nastaveny a vrátit .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> \<nebo io.h>|\<errno.h>|

## <a name="example"></a>Příklad

Tento příklad používá **_access_s** ke kontrole souboru s názvem crt_access_s.c, aby zjistil, zda existuje a zda je povoleno psaní.

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

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat funkce](stat-functions.md)
