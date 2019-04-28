---
title: _chsize_s
ms.date: 11/04/2016
apiname:
- _chsize_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: a56efe826d43c80dc2cdee295e58872e7dd3c9ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348507"
---
# <a name="chsizes"></a>_chsize_s

Změní velikost souboru. Toto je verze [_chsize –](chsize.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*fd*<br/>
Popisovač souboru odkazující na otevřený soubor.

*Velikost*<br/>
Novou velikost souboru v bajtech.

## <a name="return-value"></a>Návratová hodnota

**_chsize_s –** vrací hodnotu 0, pokud je úspěšně změněna velikost souboru. Nenulový návratová hodnota označuje chybu: Vrácená hodnota je **EACCES** Pokud zadaný soubor je uzamčen před přístupem, **EBADF** Pokud zadaný soubor je jen pro čtení nebo popisovač je neplatný, **ENOSPC** Pokud již není místo na zařízení, nebo **EINVAL** Pokud velikost je menší než nula. **errno** je nastavena na stejnou hodnotu.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Chsize_s –** rozšiřuje funkce nebo zkrátí soubor přidružený k *fd* délce určené *velikost*. Soubor musí být otevřen v režimu, který umožňuje zápis. Znaky s hodnotou Null ('\0') se připojují, pokud je soubor rozšířeno. Soubor je zkrácen, dojde ke ztrátě všech dat od konce zkrácený soubor původní délku souboru.

**_chsize_s –** trvá 64bitové celé číslo jako velikost souboru a proto dokáže zpracovat soubor velikosti větší než 4 GB. **_chsize –** je omezen velikostí 32bitového souboru.

Tato funkce ověřuje své parametry. Pokud *fd* není platným souborem popisovač nebo velikost je menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
