---
title: "_get_osfhandle – | Microsoft Docs"
ms.custom: 
ms.date: 12/12/2017
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
ms.workload: cplusplus
ms.openlocfilehash: 2b810edac60b08ccc31d6767cb11b7176fb981b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

*FD*  
Existující popisovače souborů.  
  
## <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru operačního systému, pokud *fd* je platný. Jinak se obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `INVALID_HANDLE_VALUE` (-1) a nastaví `errno` k `EBADF`, označující neplatný popisovač souboru.  
  
## <a name="remarks"></a>Poznámky

Zavřete soubor, jehož popisovač souboru operačního systému (OS) se získávají pomocí `_get_osfhandle`, volání [ \_zavřete](../../c-runtime-library/reference/close.md) na popisovače souborů *fd*. Nevolejte `CloseHandle` na návratovou hodnotu této funkce. Je vlastníkem základní popisovač souboru *fd* popisovače souborů a při zavření `_close` se volá na *fd*. Pokud je vlastníkem popisovače souborů `FILE *` datového proudu, pak volání [fclose –](../../c-runtime-library/reference/fclose-fcloseall.md) na který `FILE *` datový proud se zavře popisovače souborů a základní popisovač souboru. V takovém případě Nevolejte `_close` na popisovače souborů.
  
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
[_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
