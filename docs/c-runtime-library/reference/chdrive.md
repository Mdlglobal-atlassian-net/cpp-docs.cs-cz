---
title: _chdrive – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _chdrive
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
- chdrive
- _chdrive
dev_langs:
- C++
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f95169f62fa2eaf9c562bff463ad84c0827db9a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="chdrive"></a>_chdrive

Změní aktuální pracovní jednotce.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*Jednotka*<br/>
Celé číslo od 1 do 26, který určuje aktuální pracovní jednotky (1 = A, 2 = B a tak dále).

## <a name="return-value"></a>Návratová hodnota

Nula (0), pokud aktuální pracovní jednotky se úspěšně; změnila. jinak hodnota -1.

## <a name="remarks"></a>Poznámky

Pokud *jednotky* není v rozsahu od 1 do 26, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **_chdrive –** funkce vrátí hodnotu -1, **errno** je nastaven na **eacces –**, a **_doserrno –** je nastaven na  **ERROR_INVALID_DRIVE**.

**_Chdrive –** funkce není bezpečné pro přístup z více vláken protože závisí na **SetCurrentDirectory** funkce, které je samo není bezpečné pro přístup z více vláken. Chcete-li použít **_chdrive –** bezpečně vícevláknové aplikace, je nutné zadat vlastní synchronizace vláken. Další informace, přejděte na [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) a poté vyhledejte **SetCurrentDirectory**.

**_Chdrive –** funkce se změní pouze aktuální pracovní jednotce.  **_chdir –** změní aktuální pracovní adresář.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_chdrive**|\<Direct.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_getdrive –](getdrive.md).

## <a name="see-also"></a>Viz také

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
