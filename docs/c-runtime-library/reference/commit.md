---
title: "_commit – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _commit
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
- _commit
- commit
dev_langs:
- C++
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed5a3f1e8d1f4a122ecf5a66393fa5c1f5c65f1b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="commit"></a>_commit
Vyprázdnění souboru přímo na disku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _commit(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Popisovače souborů na otevření souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_commit` Vrátí hodnotu 0, pokud soubor byl úspěšně vyprázdněn na disk. Vrácená hodnota -1 označuje chybu.  
  
## <a name="remarks"></a>Poznámky  
 `_commit` Funkce vynutí operačního systému k zápisu soubor přidružený k `fd` na disk. Toto volání zajišťuje okamžitě, vyprázdní zadaný soubor není uvážení operačního systému.  
  
 Pokud `fd` je popisovač souboru je neplatný. obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a `errno` je nastaven na `EBADF`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|-------------|---------------------|----------------------|  
|`_commit`|\<io.h>|\<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_read](../../c-runtime-library/reference/read.md)   
 [_write](../../c-runtime-library/reference/write.md)