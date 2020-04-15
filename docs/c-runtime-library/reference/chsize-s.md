---
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 70845124eb889d73a0f87aadd923e2d86db96c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350074"
---
# <a name="_chsize_s"></a>_chsize_s

Změní velikost souboru. Toto je verze [_chsize](chsize.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*Fd*<br/>
Popisovač souboru odkazující na otevřený soubor.

*Velikost*<br/>
Nová délka souboru v bajtech.

## <a name="return-value"></a>Návratová hodnota

**_chsize_s** vrátí hodnotu 0, pokud je velikost souboru úspěšně změněna. Nenulová vrácená hodnota označuje chybu: vrácená hodnota je **EACCES,** pokud je zadaný soubor uzamčen proti přístupu, **EBADF,** pokud je zadaný soubor jen pro čtení nebo popisovač je neplatný, **ENOSPC,** pokud v zařízení nezbývá žádné místo, nebo **EINVAL,** pokud je velikost menší než nula. **errno** je nastavena na stejnou hodnotu.

Další informace o těchto a dalších návratových kódech naleznete [v tématech _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_chsize_s** rozšiřuje nebo zkrátí soubor přidružený k *fd* na délku určenou *velikostí*. Soubor musí být otevřen v režimu, který umožňuje zápis. Pokud je soubor rozšířen, jsou připojeny nulové znaky (\0). Pokud je soubor zkrácen, budou ztracena všechna data od konce zkráceného souboru do původní délky souboru.

**_chsize_s** má 64bitové celé číslo jako velikost souboru, a proto může zpracovávat velikosti souborů větší než 4 GB. **_chsize** je omezena na 32bitové velikosti souborů.

Tato funkce ověřuje její parametry. Pokud *fd* není platný popisovač souboru nebo velikost je menší než nula, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
