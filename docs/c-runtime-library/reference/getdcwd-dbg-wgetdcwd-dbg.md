---
title: _getdcwd_dbg –, _wgetdcwd_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
apitype: DLLExport
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
dev_langs:
- C++
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b9709a5dad5bd83dc34c7e2aff7cc888b7b3451
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

Ladicí verze [_getdcwd –, _wgetdcwd –](getdcwd-wgetdcwd.md) funkce (dostupné pouze při ladění).

## <a name="syntax"></a>Syntaxe

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Jednotka*<br/>
Název na disk.

*Vyrovnávací paměti*<br/>
Umístění úložiště pro cestu.

*MAXLEN*<br/>
Maximální délka cesty ve znacích: **char** pro **_getdcwd_dbg –** a **wchar_t** pro **_wgetdcwd_dbg –**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_client_block –** nebo **_normal_block –**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na *vyrovnávací paměti*. A **NULL** návratová hodnota určuje chybu, a **errno** nastavený buď na **enomem –**, označující, že je nedostatek paměti k přidělení *maxlen* bajtů (při **NULL** argument je zadána jako *vyrovnávací paměti*), nebo **erange –**, která znamená, že cesta je delší než *maxlen*  znaků. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Getdcwd_dbg –** a **_wgetdcwd_dbg –** funkce jsou stejné jako **_getdcwd –** a **_wgetdcwd –** s tím rozdílem, že když **_DEBUG –** je definován, tyto funkce používají verzi ladění **malloc –** a **_malloc_dbg –** přidělit paměť, pokud **NULL** je předán jako *vyrovnávací paměti* parametr. Další informace najdete v tématu [_malloc_dbg –](malloc-dbg.md).

Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat **_crtdbg_map_alloc –** příznak. Když **_crtdbg_map_alloc –** je definován, volání **_getdcwd –** a **_wgetdcwd –** jsou mapovány na **_getdcwd_dbg –** a **_ wgetdcwd_dbg –**, s *blockType* nastavena na **_normal_block –**. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako **_client_block –**. Další informace najdete v tématu [typy bloky v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
