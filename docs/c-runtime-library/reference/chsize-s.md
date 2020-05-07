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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: faed95bfeb6fad88f502101e166ec6124b6e591d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910418"
---
# <a name="_chsize_s"></a>_chsize_s

Změní velikost souboru. Jedná se o verzi [_chsize](chsize.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parametry

*FD*<br/>
Popisovač souboru odkazující na otevřený soubor.

*hodnota*<br/>
Nová délka souboru v bajtech

## <a name="return-value"></a>Návratová hodnota

**_chsize_s** vrátí hodnotu 0, pokud je velikost souboru úspěšně změněna. Nenulová návratová hodnota označuje chybu: vrácená hodnota je **EACCES** , pokud je zadaný soubor uzamčený proti přístupu, **EBADF** Pokud je zadaný soubor jen pro čtení, nebo je popisovač neplatný, **ENOSPC** Pokud na zařízení není žádné místo, nebo **EINVAL** , pokud je velikost menší než nula. **errno** je nastavená na stejnou hodnotu.

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_chsize_s** rozšiřuje nebo zkrátí soubor přidružený k *FD* na délku určenou *velikostí*. Soubor musí být otevřen v režimu, který povoluje zápis. Pokud je soubor rozšířený, připojí se znaky null (' \ 0 '). Pokud je soubor zkrácený, ztratí se všechna data z konce zkráceného souboru do původní délky souboru.

**_chsize_s** jako velikost souboru přebírá 64 celé číslo, a proto může zpracovávat velikosti souborů větší než 4 GB. **_chsize** je omezen na 32 souborů.

Tato funkce ověří své parametry. Pokud není *FD* platný popisovač souboru nebo je menší než nula, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<IO. h>|\<errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
