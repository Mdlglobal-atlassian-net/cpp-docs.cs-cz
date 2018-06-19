---
title: __dllonexit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __dllonexit
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
f1_keywords:
- __dllonexit
dev_langs:
- C++
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c0105ccc5a40c4e5fe789814adfabe6c9749650
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450716"
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
 V případě úspěšného ukazatel na funkci uživatele. V opačném **NULL** ukazatel.  
  
## <a name="remarks"></a>Poznámky  
 `__dllonexit` Funkce je obdobou [_onexit –](../c-runtime-library/reference/onexit-onexit-m.md) fungovat s tím rozdílem, že globální proměnné použije tato funkce nejsou viditelné pro tuto rutinu. Místo globální proměnné, tato funkce používá `pbegin` a `pend` parametry.  
  
 `_onexit` a `atexit` funkce v knihovně DLL propojené s MSVCRT. LIB musí spravovat vlastní seznam atexit/_onexit –. Tato rutina je pracovní proces, který získá volá tyto knihovny DLL.  
  
 `_PVFV` Typ je definován jako `typedef void (__cdecl *_PVFV)(void)`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný soubor|  
|-------------|-------------------|  
|__dllonexit|onexit.c|  
  
## <a name="see-also"></a>Viz také  
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)