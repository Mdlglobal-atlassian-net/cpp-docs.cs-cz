---
title: _chsize_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d131f5e21fa4980e77cfb9dc858d5329b94e2b93
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="chsizes"></a>_chsize_s

Změní velikost souboru. Toto je verze [_chsize –](chsize.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Odkaz na soubor otevřený popisovač souboru.

*Velikost*<br/>
Nové délka souboru v bajtech.

## <a name="return-value"></a>Návratová hodnota

**_chsize_s –** vrátí hodnotu 0, pokud velikost souboru je úspěšně změnit. Vrácená nenulová hodnota označuje chybu: Vrácená hodnota je **eacces –** zadaný soubor uzamčen před přístupem, **ebadf –** Pokud zadaný soubor je jen pro čtení nebo je neplatná, popisovač **Enospc –** Pokud žádné místa v zařízení, nebo **einval –** Pokud velikost je menší než nula. **errno** je nastaven na stejnou hodnotu.

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Chsize_s –** funkce rozšiřuje nebo zkrátí soubor přidružený k *fd* na délku určeného *velikost*. Soubor musí být otevřený v režimu, která umožňuje zápis. Znaky Null (\0) jsou připojeny, pokud je soubor rozšířeno. Soubor se zkrátí, dojde ke ztrátě všech dat od konce souboru zkrácená na původní délku souboru.

**_chsize_s –** trvá 64bitové celé číslo jako velikost souboru a proto dokáže zpracovat velikost souboru je větší než 4 GB. **_chsize –** je omezený na velikosti souborů 32-bit.

Tato funkce ověří jeho parametry. Pokud *fd* není platný soubor popisovače nebo velikost je menší než nula, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<IO.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
