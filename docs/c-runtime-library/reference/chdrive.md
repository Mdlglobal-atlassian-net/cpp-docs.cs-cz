---
title: "_chdrive – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1290f5a29ce2b6d80f98889fbb0fc5709cfa43e4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="chdrive"></a>_chdrive
Změní aktuální pracovní jednotce.  
  
> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _chdrive(   
   int drive   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `drive`  
 Celé číslo od 1 do 26, který určuje aktuální pracovní jednotky (1 = A, 2 = B a tak dále).  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula (0), pokud aktuální pracovní jednotky se úspěšně; změnila. jinak hodnota -1.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `drive` není v rozsahu od 1 do 26, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **_chdrive –** funkce vrátí hodnotu -1, `errno` je nastaven na `EACCES`, a `_doserrno` je nastaven na `ERROR_INVALID_DRIVE`.  
  
 **_Chdrive –** funkce není bezpečné pro přístup z více vláken protože závisí na **SetCurrentDirectory** funkce, které je samo není bezpečné pro přístup z více vláken. Chcete-li použít **_chdrive –** bezpečně vícevláknové aplikace, je nutné zadat vlastní synchronizace vláken. Další informace, přejděte na [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) a poté vyhledejte **SetCurrentDirectory**.  
  
 **_Chdrive –** funkce se změní pouze aktuální pracovní jednotce.  **_chdir –** změní aktuální pracovní adresář.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|**_chdrive**|\<direct.h>|  
  
 Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_getdrive –](../../c-runtime-library/reference/getdrive.md).  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)   
 [_chdir, _wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getcwd, _wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [_mkdir, _wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_rmdir, _wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)