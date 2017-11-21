---
title: "_get_osfhandle – | Microsoft Docs"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
dev_langs: C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e3b15b4577d1d8c0b24df82acff76494474c4e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="getosfhandle"></a>_get_osfhandle

Načte popisovač souboru operačního systému, který je přidružen popisovač zadaný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
### <a name="parameters"></a>Parametry

*FD* existující soubor popisovače.  
  
## <a name="return-value"></a>Návratová hodnota

Zpracování souboru operačního systému, pokud *fd* je platný. Jinak se obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `INVALID_HANDLE_VALUE` (-1) a nastaví `errno` k `EBADF`, označující neplatný popisovač souboru.  
  
## <a name="remarks"></a>Poznámky

Zavřete soubor, jehož popisovač souboru operačního systému se získávají pomocí `_get_osfhandle`, volání [ \_zavřete](../../c-runtime-library/reference/close.md) na popisovače souborů *fd*. Základní obslužná rutina také uzavřené volání `_close`, takže není nutné volat funkci Win32 `CloseHandle` na původní popisovač.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_osfhandle`|\<IO.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)   
[_close –](../../c-runtime-library/reference/close.md)   
[_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
[_dup –, _dup2 –](../../c-runtime-library/reference/dup-dup2.md)   
[_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)
