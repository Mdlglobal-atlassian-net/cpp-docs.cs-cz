---
title: _chdrive
ms.date: 11/04/2016
api_name:
- _chdrive
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
ms.openlocfilehash: 3ee292c03c9d31944e0a555c2159d7a5dd2cd0eb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939244"
---
# <a name="_chdrive"></a>_chdrive

Změní aktuální pracovní jednotku.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>Parametry

*drive*<br/>
Celé číslo od 1 do 26, které určuje aktuální pracovní jednotku (1 = A, 2 = B a tak dále).

## <a name="return-value"></a>Návratová hodnota

Nula (0), pokud se aktuální pracovní jednotka úspěšně změnila; v opačném případě-1.

## <a name="remarks"></a>Poznámky

Pokud *jednotka* není v rozsahu od 1 do 26, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce **_chdrive** vrátí hodnotu-1, **errno** je nastavená na **EACCES**a **_doserrno** je nastavená na **ERROR_INVALID_DRIVE**.

Funkce **_chdrive** není bezpečná pro přístup z více vláken, protože závisí na funkci **SetCurrentDirectory** , která sama o sobě není bezpečná pro přístup z více vláken. Chcete-li v aplikaci s více vlákny používat **_chdrive** bezpečně, je nutné poskytnout vlastní synchronizaci vláken. Další informace najdete v tématu [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory).

Funkce **_chdrive** mění pouze aktuální pracovní jednotku;  **_chdir** změní aktuální pracovní adresář.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_chdrive**|\<Direct. h >|

Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_getdrive](getdrive.md).

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
