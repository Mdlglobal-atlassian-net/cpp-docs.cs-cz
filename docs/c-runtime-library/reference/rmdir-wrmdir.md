---
title: _rmdir –, _wrmdir – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1532aebb588ca67316a1317e0d27184309a5701
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
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

*adresář*<br/>
Cestu k adresáři odeberou.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud se úspěšně odstranil adresář. Vrácená hodnota -1 označuje chybu a **errno** nastaven na jednu z následujících hodnot:

|errno – hodnota|Podmínka|
|-|-|
**ENOTEMPTY**|Zadaná cesta není adresář, adresář není prázdný, nebo adresář je aktuální pracovní adresář nebo kořenový adresář.
**ENOENT –**|Cesta je neplatná.
**EACCES –**|Program má otevřený popisovač k adresáři.

Další informace o těchto a dalších návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Rmdir –** funkce odstraní adresář zadaný *adresář*. Adresář musí být prázdný a nesmí být aktuální pracovní adresář nebo kořenový adresář.

**_wrmdir –** je verze široká charakterová **_rmdir –**; *adresář* argument **_wrmdir –** je široká charakterová řetězec. **_wrmdir –** a **_rmdir –** chovat jinak shodně.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_trmdir –**|**_rmdir**|**_rmdir**|**_wrmdir**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_rmdir**|\<Direct.h >|
|**_wrmdir**|\<Direct.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_mkdir –](mkdir-wmkdir.md).

## <a name="see-also"></a>Viz také

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
