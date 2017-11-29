---
title: "_close – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _close
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
f1_keywords: _close
dev_langs: C++
helpviewer_keywords:
- _close function
- close function
- files [C++], closing
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f46560346718016af015410730696e766afa5c9a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="close"></a>_close
Zavře soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _close(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Popisovače souborů na otevření souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_close`Vrátí hodnotu 0, pokud soubor se zavřel úspěšně. Vrácená hodnota -1 označuje chybu.  
  
## <a name="remarks"></a>Poznámky  
 `_close` Funkce zavře soubor přidružený k `fd`.  
  
 Jsou uzavřeny popisovače souborů a základní popisovač souboru. Proto není nutné volat `CloseHandle` Pokud soubor byl původně otevřít pomocí funkce Win32 `CreateFile` a převést na popisovač souboru pomocí `_open_osfhandle`.  
  
 Tato funkce ověří jeho parametry. Pokud `fd` popisovač chybného souboru, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a `errno` je nastaven na `EBADF`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_close`|\<IO.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_Otevřít](../../c-runtime-library/reference/open-wopen.md).  
  
## <a name="see-also"></a>Viz také  
 [I/O nízké úrovně](../../c-runtime-library/low-level-i-o.md)   
 [_chsize –](../../c-runtime-library/reference/chsize.md)   
 [_creat –, _wcreat –](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup –, _dup2 –](../../c-runtime-library/reference/dup-dup2.md)   
 [_Otevřít _wopen –](../../c-runtime-library/reference/open-wopen.md)   
 [_unlink –, _wunlink –](../../c-runtime-library/reference/unlink-wunlink.md)