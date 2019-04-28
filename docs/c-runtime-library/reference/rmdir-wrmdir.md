---
title: _rmdir, _wrmdir
ms.date: 11/04/2016
apiname:
- _wrmdir
- _rmdir
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
- trmdir
- _trmdir
- wrmdir
- _rmdir
- _wrmdir
helpviewer_keywords:
- _rmdir function
- directories [C++], deleting
- rmdir function
- directories [C++], removing
- trmdir function
- _trmdir function
- _wrmdir function
- wrmdir function
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
ms.openlocfilehash: 0d0d9a25b70746174a66abbe088b297a5d9a0942
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357457"
---
# <a name="rmdir-wrmdir"></a>_rmdir, _wrmdir

Odstraní adresář.

## <a name="syntax"></a>Syntaxe

```C
int _rmdir(
   const char *dirname
);
int _wrmdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parametry

*DirName*<br/>
Cesta adresáře, která se má odebrat.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud adresáře se úspěšně odstranil. Návratová hodnota-1 označuje chybu a **errno** nastavena na jednu z následujících hodnot:

|Hodnota errno|Podmínka|
|-|-|
| **ENOTEMPTY** | Danou cestu není adresář, adresář není prázdný nebo adresář je aktuální pracovní adresář nebo kořenový adresář. |
| **ENOENT** | Cesta je neplatná. |
| **EACCES** | Program má otevřený popisovač do adresáře. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Rmdir –** funkce odstraní adresář zadaný *dirname*. Adresář musí být prázdný a nesmí být aktuálního pracovního adresáře nebo do kořenového adresáře.

**_wrmdir –** je verze širokého znaku **_rmdir –**; *dirname* argument **_wrmdir –** je širokoznaký řetězec. **_wrmdir –** a **_rmdir –** se jinak chovají stejně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_rmdir**|\<direct.h>|
|**_wrmdir**|\<Direct.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_mkdir –](mkdir-wmkdir.md).

## <a name="see-also"></a>Viz také:

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
