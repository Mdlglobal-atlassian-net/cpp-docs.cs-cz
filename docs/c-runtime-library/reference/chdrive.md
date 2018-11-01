---
title: _chdrive
ms.date: 11/04/2016
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
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 963b7b7b40b632981abfc1529beb9c48a5b991ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602303"
---
# <a name="chdrive"></a>_chdrive

Změní aktuální pracovní jednotku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*Jednotky*<br/>
Celé číslo od 1 až 26, který určuje aktuální pracovní jednotku (1 = A, 2 = B a tak dále).

## <a name="return-value"></a>Návratová hodnota

Nula (0), pokud aktuální pracovní jednotka byla změněna úspěšně; jinak -1.

## <a name="remarks"></a>Poznámky

Pokud *jednotky* není v rozsahu 1 až 26, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **_chdrive –** funkce vrátí hodnotu -1, **errno** je nastavena na **EACCES**, a **_doserrno** je nastavena na  **ERROR_INVALID_DRIVE**.

**_Chdrive –** funkce není bezpečná pro vlákno protože závisí **SetCurrentDirectory** funkce, která sama o sobě není bezpečná pro vlákno. Chcete-li použít **_chdrive –** bezpečně ve vícevláknové aplikaci, je nutné zadat vlastní synchronizaci vláken. Další informace najdete v tématu [SetCurrentDirectory](/windows/desktop/api/winbase/nf-winbase-setcurrentdirectory).

**_Chdrive –** funkce se změní pouze aktuální pracovní jednotku;  **_chdir –** změní aktuální pracovní adresář.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_chdrive**|\<Direct.h >|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_getdrive –](getdrive.md).

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
