---
title: "_Crtmemdumpallobjectssince – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs: C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d71b5d13b5616717c0b3fc0ac6eae0fc1ca8b551
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince
Vypíše informace o objektech v haldě od začátku spuštění programu, nebo ze stavu zadaného haldy (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `state`  
 Ukazatele stavu haldy zahájíte vypsání z nebo **NULL**.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtMemDumpAllObjectsSince` Funkce výpisy ladění informace hlavičky objektů přidělené v haldě ve formě uživatelem čitelný. Informace o výpisu lze aplikace ke sledování přidělování a zjišťování problémů paměti. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtMemDumpAllObjectsSince` jsou odebrány při předběžném zpracování.  
  
 `_CrtMemDumpAllObjectsSince`používá hodnotu `state` parametr k určení, kam inicializace operace výpisu. Zahájíte vypsání ze zadaného haldy stavu, `state` parametr musí být ukazatel na **_crtmemstate –** struktura, která má byla vyplněna objektem [_crtmemcheckpoint –](../../c-runtime-library/reference/crtmemcheckpoint.md) před `_CrtMemDumpAllObjectsSince` byl volá se. Když `state` je **NULL**, funkce začne výpisu od začátku spuštění programu.  
  
 Pokud je aplikace nainstalována funkce háku výpisu voláním [_crtsetdumpclient –](../../c-runtime-library/reference/crtsetdumpclient.md), potom pokaždé, když `_CrtMemDumpAllObjectsSince` Vypíše informace o `_CLIENT_BLOCK` typ bloku, zavolá funkci výpisu zadané aplikace. Ve výchozím nastavení, interní bloky C Runtime (`_CRT_BLOCK`) nejsou zahrnuty do operace výpisu paměti. [_Crtsetdbgflag –](../../c-runtime-library/reference/crtsetdbgflag.md) funkce slouží k zapnutí `_CRTDBG_CHECK_CRT_DF` bit z **_crtdbgflag –** zahrnout tyto bloky. Kromě toho bloky označen jako vydání nebo ignorovat (**_free_block –**, **_ignore_block –**) nejsou součástí výpis stavu paměti.  
  
 Další informace o stavu funkce hald a `_CrtMemState` struktury najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Další informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|**_CrtMemDumpAll ObjectsSince**|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `_CrtMemDumpAllObjectsSince`, najdete v části [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167).  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)