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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c3893b3d78a2c142ffc9e10eb6bbf299c5fddb9b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916900"
---
# <a name="_access_s-_waccess_s"></a>_access_s, _waccess_s

Určuje oprávnění ke čtení a zápisu souborů. Jedná se o verzi [_access, _waccess](access-waccess.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*dílčí*<br/>
Cesta k souboru nebo adresáři.

*Mode*<br/>
Nastavení oprávnění.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí hodnotu 0, pokud soubor má daný režim. Funkce vrátí kód chyby, pokud pojmenovaný soubor neexistuje nebo není přístupný v daném režimu. V tomto případě funkce vrátí kód chyby ze sady následovně a také nastaví `errno` stejnou hodnotu.

|hodnota errno|Podmínka|
|-|-|
`EACCES`|Přístup se odepřel. Nastavení oprávnění souboru nepovoluje zadaný přístup.
`ENOENT`|Název souboru nebo cesta nebyla nalezena.
`EINVAL`|Neplatný parametr

Další informace najdete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Při použití se soubory funkce **_access_s** určuje, zda zadaný soubor existuje a je k němu možné přistupovat, jak je určeno hodnotou *Mode*. Při použití s adresáři **_access_s** určuje pouze to, zda existuje zadaný adresář. Ve Windows 2000 a novějších operačních systémech mají všechny adresáře přístup pro čtení a zápis.

|hodnota režimu|Kontroluje soubor pro|
|----------------|---------------------|
|00|Pouze existence.|
|02|Oprávnění k zápisu.|
|04|Oprávnění číst.|
|06|Oprávnění ke čtení a zápisu.|

Oprávnění ke čtení nebo zápisu souboru není dostatečné, aby bylo možné zajistit možnost otevřít soubor. Například pokud je soubor uzamčen jiným procesem, nemusí být přístupný, i když **_access_s** vrátí hodnotu 0.

**_waccess_s** je verze **_access_s**s velkým znakem, kde argument *cesty* pro **_waccess_s** je řetězec s velkým znakem. V opačném případě **_waccess_s** a **_access_s** se chovají stejně.

Tyto funkce ověřují své parametry. Pokud je *cesta* null nebo *režim* neurčuje platný režim, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví `errno` na `EINVAL` a vrátí. `EINVAL`

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_access_s**|\<IO. h>|\<errno. h>|
|**_waccess_s**|\<WCHAR. h> nebo \<IO. h>|\<errno. h>|

## <a name="example"></a>Příklad

Tento příklad používá **_access_s** ke kontrole souboru s názvem crt_access_s. c, aby bylo možné zjistit, zda existuje a zda je zápis povolen.

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
