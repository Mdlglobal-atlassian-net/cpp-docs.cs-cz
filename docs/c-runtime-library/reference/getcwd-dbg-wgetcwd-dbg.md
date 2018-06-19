---
title: _getcwd_dbg –, _wgetcwd_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
dev_langs:
- C++
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b4124b5825f27ec26afdb40f0ccc9e4de4ed087
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401552"
---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg, _wgetcwd_dbg

Ladicí verze [_getcwd –, _wgetcwd –](getcwd-wgetcwd.md) funkce (dostupné pouze při ladění).

## <a name="syntax"></a>Syntaxe

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Umístění úložiště pro cestu.

*MAXLEN*<br/>
Maximální délka cesty ve znacích: **char** pro **_getcwd_dbg –** a **wchar_t** pro **_wgetcwd_dbg –**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_client_block –** nebo **_normal_block –**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na *vyrovnávací paměti*. A **NULL** návratová hodnota určuje chybu, a **errno** nastavený buď na **enomem –**, označující, že je nedostatek paměti k přidělení *maxlen* bajtů (při **NULL** argument je zadána jako *vyrovnávací paměti*), nebo **erange –**, která znamená, že cesta je delší než *maxlen*  znaků.

Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getcwd_dbg –** a **_wgetcwd_dbg –** funkce jsou stejné jako **_getcwd –** a **_wgetcwd –** s tím rozdílem, že když **_ LADĚNÍ** je definován, tyto funkce používají verzi ladění **malloc –** a **_malloc_dbg –** přidělit paměť, pokud **NULL** se předá jako první parametr. Další informace najdete v tématu [_malloc_dbg –](malloc-dbg.md).

Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat **_crtdbg_map_alloc –** příznak. Když **_crtdbg_map_alloc –** je definován, volání **_getcwd –** a **_wgetcwd –** jsou mapovány na **_getcwd_dbg –** a **_ wgetcwd_dbg –**, s *blockType* nastavena na **_normal_block –**. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako **_client_block –**. Další informace najdete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

## <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
