---
title: "_Crtmemdumpstatistics – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
dev_langs: C++
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d1c5192d3770a520a26bd7d9fd532f412a3e153
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics
Vypíše informace hlavičky ladění pro zadaný stav haldy ve formě čitelné pro uživatele (pouze pro ladicí verzi).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _CrtMemDumpStatistics(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `state`  
 Ukazatel na stav haldy pro výpis.  
  
## <a name="remarks"></a>Poznámky  
 Funkce `_CrtMemDumpStatistics` vypíše informace hlavičky ladění pro určitý stav haldy ve formě čitelné uživatelem. Pomocí statistiky výpisu lze v aplikaci sledovat přidělování a vyhledávat problémy s pamětí. Stav paměti může obsahovat specifický stav haldy nebo rozdíl mezi dvěma stavy. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtMemDumpStatistics` jsou odebrány při předběžném zpracování.  
  
 `state` Parametr musí být ukazatel na `_CrtMemState` struktura, která má byla vyplněna objektem [_crtmemcheckpoint –](../../c-runtime-library/reference/crtmemcheckpoint.md) nebo vrácený [_crtmemdifference –](../../c-runtime-library/reference/crtmemdifference.md) před `_CrtMemDumpStatistics` je volána. Pokud `state` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je zpracování povoleno pokračovat, je proměnná `errno` nastavena na hodnotu `EINVAL` a nedojde k žádné akci. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Další informace o stavu funkce hald a `_CrtMemState` struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|  
|-------------|---------------------|----------------------|  
|`_CrtMemDumpStatistics`|\<crtdbg.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
 **Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)