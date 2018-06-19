---
title: _getdcwd –, _wgetdcwd – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getdcwd
- _wgetdcwd
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
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
dev_langs:
- C++
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0ccc526b196982402ca3b795276df8c790ad35a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404246"
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd, _wgetdcwd

Získá úplnou cestu aktuálního pracovního adresáře na určené jednotce.

## <a name="syntax"></a>Syntaxe

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parametry

*Jednotka*<br/>
Kladné celé číslo, které určuje jednotku, která (0 = výchozí jednotce, 1 = A, 2 = B a tak dále).

Pokud má určená jednotka není k dispozici, nebo typ jednotky (například vyměnitelné, pevné, disku CD-ROM, RAM disku nebo síťové jednotky) nelze určit, obslužné rutiny neplatný parametr, který je popsaný v [ověření parametru](../../c-runtime-library/parameter-validation.md), je vyvolat.

*Vyrovnávací paměti*<br/>
Umístění úložiště pro danou cestu nebo **NULL**.

Pokud **NULL** není zadaný, tato funkce přiděluje vyrovnávací paměti alespoň *maxlen* velikost pomocí **malloc –** a vrátí hodnotu, která **_getdcwd –** je ukazatel na přidělené vyrovnávací paměti. Vyrovnávací paměť může být uvolněno voláním **volné** a předání ukazatele.

*MAXLEN*<br/>
Nenulové hodnoty kladné celé číslo, které určuje maximální délku cesty, ve znacích: **char** pro **_getdcwd –** a **wchar_t** pro **_wgetdcwd –**.

Pokud *maxlen* není větší než nula, obslužné rutiny neplatný parametr, který je popsaný v [ověření parametru](../../c-runtime-library/parameter-validation.md), je vyvolána.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který představuje úplnou cestu aktuálního pracovního adresáře na určené jednotce, nebo **NULL**, což označuje chybu.

Pokud *vyrovnávací paměti* je zadán jako **NULL** a není dostatek paměti k přidělení *maxlen* znaků, dojde k chybě a **errno** je Nastavte na **enomem –**. Délka cesty, která obsahuje ukončující znak hodnoty null, překročí-li *maxlen*, dojde k chybě a **errno** je nastaven na **erange –**. Další informace o tyto kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getdcwd –** funkce získá úplnou cestu aktuálního pracovního adresáře na určené jednotce a ukládá je v *vyrovnávací paměti*. Pokud aktuální pracovní adresář se nastaví na kořen, řetězec končí zpětné lomítko (\\). Pokud aktuální pracovní adresář je nastavena do jiného adresáře než je kořenový adresář, ukončí řetězec s názvem adresáře a nikoli s lomítkem.

**_wgetdcwd –** je verze široká charakterová **_getdcwd –** a jeho *vyrovnávací paměti* parametr a návratové hodnoty jsou široká charakterová řetězce. V opačném **_wgetdcwd –** a **_getdcwd –** chovají stejně jako.

Tato funkce je bezpečné pro přístup z více vláken, i když závisí na **GetFullPathName**, který je sám není bezpečné pro přístup z více vláken. Ale porušení zabezpečení vlákna Pokud vícevláknové aplikace volá obě tato funkce a **GetFullPathName**. Další informace, přejděte na [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) a poté vyhledejte **GetFullPathName**.

Verze této funkce, který má **jazyka _nolock** přípona se chová stejně tuto funkci s tím rozdílem, že není bezpečné pro přístup z více vláken a není chráněn z narušení jiná vlákna. Další informace najdete v tématu [_getdcwd_nolock –, _wgetdcwd_nolock –](getdcwd-nolock-wgetdcwd-nolock.md).

Když **_DEBUG –** a **_crtdbg_map_alloc –** jsou definovány, volání **_getdcwd –** a **_wgetdcwd –** jsou nahrazovány volání **_getdcwd_dbg –** a **_wgetdcwd_dbg –** tak, že ladíte přidělení paměti. Další informace najdete v tématu[_getdcwd_dbg –, _wgetdcwd_dbg –](getdcwd-dbg-wgetdcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdcwd**|\<Direct.h >|
|**_wgetdcwd**|\<Direct.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_getdrive –](getdrive.md).

## <a name="see-also"></a>Viz také

[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
