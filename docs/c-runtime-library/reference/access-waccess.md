---
title: _přístupový _waccess – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _access
- _waccess
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
- _waccess
- _access
- taccess
- waccess
- _taccess
dev_langs:
- C++
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1e8e4d8be25a175f40d59aa3d3b8eb1ecbf4c3e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097013"
---
# <a name="access-waccess"></a>_access, _waccess

Určuje, zda je soubor jen pro čtení, nebo ne. Bezpečnější verze jsou k dispozici. Zobrazit [_access_s – _waccess_s –](access-s-waccess-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parametry

*Cesta*<br/>
Cesta k souboru nebo adresáře.

*Režim*<br/>
Atribut pro čtení a zápisu.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí hodnotu 0, pokud má soubor dané režimu. Funkce vrátí hodnotu -1, pokud pojmenovaný soubor neexistuje nebo nemá daný režimu. v takovém případě `errno` je nastavit, jak je znázorněno v následující tabulce.

|||
|-|-|
`EACCES`|Přístup byl odepřen: nastavení oprávnění k souboru neumožňuje zadaný přístup.
`ENOENT`|Název souboru nebo cesta nebyla nalezena.
`EINVAL`|Neplatný parametr.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Při použití s soubory, **_přístupový** funkce určuje, jestli určený soubor nebo adresář existuje a má atributy určené hodnotou *režimu*. Při použití s adresáři, **_přístupový** pouze určuje, zda existuje zadaný adresář, ve Windows 2000 a novějších operačních systémů, všechny adresáře čtení a zápisu přístup.

|*režim* hodnota|Soubor kontroly|
|------------------|---------------------|
|00|Pouze existence|
|02|Pouze pro zápis|
|04|jen pro čtení|
|06|Čtení a zápis|

Tato funkce pouze ověří, zda souborů a adresářů jsou jen pro čtení nebo Ne, nekontroluje nastavení zabezpečení systému souborů. K tomu budete potřebovat přístupový token. Další informace o zabezpečení systému souborů najdete v tématu [přístupové tokeny](/windows/desktop/SecAuthZ/access-tokens). Třídy knihovny ATL existuje tuto funkčnost; Zobrazit [caccesstoken – třída](../../atl/reference/caccesstoken-class.md).

**_waccess –** je verze širokého znaku **_přístupový**; *cesta* argument **_waccess –** je širokoznaký řetězec. **_waccess –** a **_přístupový** se jinak chovají stejně.

Tato funkce ověřuje své parametry. Pokud *cesta* má hodnotu NULL nebo *režimu* neurčuje platný režim, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce nastaví `errno` k `EINVAL` a vrátí hodnotu -1.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**_access**|\<IO.h >|\<errno.h>|
|**_waccess**|\<wchar.h > nebo \<io.h >|\<errno.h>|

## <a name="example"></a>Příklad

Následující příklad používá **_přístupový** zkontrolovat soubor s názvem crt_ACCESS. C, zda existuje a zda je povolen zápis.

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat – funkce](stat-functions.md)