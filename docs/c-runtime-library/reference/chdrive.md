---
title: _chdrive
ms.date: 4/2/2020
api_name:
- _chdrive
- _o__chdrive
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
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 0c19fefcf6a766842ee2e25cbe6bdb61bbf48e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333350"
---
# <a name="_chdrive"></a>_chdrive

Změní aktuální pracovní jednotku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*Jednotky*<br/>
Celé číslo od 1 do 26, které určuje aktuální pracovní jednotku (1 = A, 2 = B a tak dále).

## <a name="return-value"></a>Návratová hodnota

Nula (0), pokud byla aktuální pracovní jednotka úspěšně změněna; jinak -1.

## <a name="remarks"></a>Poznámky

Pokud *jednotka* není v rozsahu od 1 do 26, obslužná rutina neplatného parametru je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce **_chdrive** vrátí -1, **errno** je nastavena na **EACCES**a **_doserrno** je nastavena na **ERROR_INVALID_DRIVE**.

Funkce **_chdrive** není bezpečná pro přístup z více vláken, protože závisí na funkci **SetCurrentDirectory,** která sama o sobě není bezpečná pro přístup z více vláken. Chcete-li bezpečně používat **_chdrive** v aplikaci s více vlákny, je nutné zadat vlastní synchronizaci vláken. Další informace naleznete v tématu [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

Funkce **_chdrive** změní pouze aktuální pracovní jednotku;  **_chdir** změní aktuální pracovní adresář.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

Další informace naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [_getdrive](getdrive.md).

## <a name="see-also"></a>Viz také

[Řízení adresářů](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
