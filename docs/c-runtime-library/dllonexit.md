---
title: __dllonexit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords: __dllonexit
dev_langs: C++
helpviewer_keywords: __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9e59acec12c90d101ef385c379c092c7034f1ed0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dllonexit"></a>__dllonexit
Zaregistruje rutinu, která má být volána v době ukončení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_onexit_t __dllonexit(   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `func`  
 Ukazatel na funkci, kterou chcete provést po ukončení.  
  
 `pbegin`  
 Ukazatel na proměnné, která odkazuje na začátku seznamu funkcí pro spuštění ve odpojit.  
  
 `pend`  
 Ukazatel na proměnné, která odkazuje na konec seznamu funkcí pro spuštění ve odpojit.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ukazatel na funkci uživatele. Jinak hodnota ukazatele s hodnotou NULL.  
  
## <a name="remarks"></a>Poznámky  
 `__dllonexit` Funkce je obdobou [_onexit –](../c-runtime-library/reference/onexit-onexit-m.md) fungovat s tím rozdílem, že globální proměnné použije tato funkce nejsou viditelné pro tuto rutinu. Místo globální proměnné, tato funkce používá `pbegin` a `pend` parametry.  
  
 `_onexit` a `atexit` funkce v knihovně DLL propojené s MSVCRT. LIB musí spravovat vlastní seznam atexit/_onexit –. Tato rutina je pracovní proces, který získá volá tyto knihovny DLL.  
  
 `_PVFV` Typ je definován jako `typedef void (__cdecl *_PVFV)(void)`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný soubor|  
|-------------|-------------------|  
|__dllonexit|onexit.c|  
  
## <a name="see-also"></a>Viz také  
 [_onexit –, _onexit_m –](../c-runtime-library/reference/onexit-onexit-m.md)