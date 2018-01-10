---
title: "_getdcwd –, _wgetdcwd – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e314db740322fc3d5e7df5aeb6bd7de747e77695
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd, _wgetdcwd
Získá úplnou cestu aktuálního pracovního adresáře na určené jednotce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `drive`  
 Kladné celé číslo, které určuje jednotku, která (0 = výchozí jednotce, 1 = A, 2 = B a tak dále).  
  
 Pokud má určená jednotka není k dispozici, nebo typ jednotky (například vyměnitelné, pevné, disku CD-ROM, RAM disku nebo síťové jednotky) nelze určit, obslužné rutiny neplatný parametr, který je popsaný v [ověření parametru](../../c-runtime-library/parameter-validation.md), je vyvolat.  
  
 `buffer`  
 Umístění úložiště pro danou cestu nebo **NULL**.  
  
 Pokud **NULL** není zadaný, tato funkce přiděluje vyrovnávací paměti alespoň `maxlen` velikost pomocí **malloc –**a vrátí hodnotu, která `_getdcwd` ukazatel do přidělené vyrovnávací paměti. Vyrovnávací paměť může být uvolněno voláním `free` a předání ukazatele.  
  
 `maxlen`  
 Nenulové hodnoty kladné celé číslo, které určuje maximální délku cesty, ve znacích: `char` pro `_getdcwd` a `wchar_t` pro `_wgetdcwd`.  
  
 Pokud `maxlen` není větší než nula, obslužné rutiny neplatný parametr, který je popsaný v [ověření parametru](../../c-runtime-library/parameter-validation.md), je vyvolána.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na řetězec, který představuje úplnou cestu aktuálního pracovního adresáře na určené jednotce, nebo `NULL`, což označuje chybu.  
  
 Pokud `buffer` je zadán jako `NULL` a není dostatek paměti k přidělení `maxlen` znaků, dojde k chybě a `errno` je nastaven na `ENOMEM`. Délka cesty, která obsahuje ukončující znak hodnoty null, překročí-li `maxlen`, dojde k chybě a `errno` je nastaven na `ERANGE`. Další informace o tyto kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_getdcwd` Funkce získá úplnou cestu aktuálního pracovního adresáře na určené jednotce a ukládá je v `buffer`. Pokud aktuální pracovní adresář se nastaví na kořen, řetězec končí zpětné lomítko (\\). Pokud aktuální pracovní adresář je nastavena do jiného adresáře než je kořenový adresář, ukončí řetězec s názvem adresáře a nikoli s lomítkem.  
  
 `_wgetdcwd`široká charakterová verze `_getdcwd`a jeho `buffer` parametr a návratové hodnoty jsou široká charakterová řetězce. V opačném `_wgetdcwd` a `_getdcwd` chovají stejně jako.  
  
 Tato funkce je bezpečné pro přístup z více vláken, i když závisí na **GetFullPathName**, který je sám není bezpečné pro přístup z více vláken. Ale porušení zabezpečení vlákna Pokud vícevláknové aplikace volá obě tato funkce a **GetFullPathName**. Další informace, přejděte na [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) a poté vyhledejte **GetFullPathName**.  
  
 Verze této funkce, který má `_nolock` přípona se chová stejně tuto funkci s tím rozdílem, že není bezpečné pro přístup z více vláken a není chráněn z narušení jiná vlákna. Další informace najdete v tématu [_getdcwd_nolock –, _wgetdcwd_nolock –](../../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md).  
  
 Když `_DEBUG` a `_CRTDBG_MAP_ALLOC` jsou definovány, volání `_getdcwd` a `_wgetdcwd` jsou nahrazovány volání `_getdcwd_dbg` a `_wgetdcwd_dbg` tak, že ladíte přidělení paměti. Další informace najdete v tématu[_getdcwd_dbg –, _wgetdcwd_dbg –](../../c-runtime-library/reference/getdcwd-dbg-wgetdcwd-dbg.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetdcwd`|`_getdcwd`|`_getdcwd`|`_wgetdcwd`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_getdcwd`|\<Direct.h >|  
|`_wgetdcwd`|\<Direct.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [_getdrive –](../../c-runtime-library/reference/getdrive.md).  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)   
 [_chdir –, _wchdir –](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_getcwd –, _wgetcwd –](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdrive –](../../c-runtime-library/reference/getdrive.md)   
 [_mkdir –, _wmkdir –](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir, _wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)