---
title: "_Crtgetdumpclient – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtGetDumpClient
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
- CrtGetDumpClient
- _CrtGetDumpClient
dev_langs: C++
helpviewer_keywords:
- _CrtGetDumpClient function
- CrtGetDumpClient function
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2bd7ff7ee99af78dba98e537a1c26b74ed5ed79c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtgetdumpclient"></a>_CrtGetDumpClient
Načte aktuální definované aplikací funkce pro vypsání `_CLIENT_BLOCK` zadejte bloky paměti (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí aktuální výpisu rutiny.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtGetDumpClient` Funkce načte aktuální funkce háku pro vypsání objekty uložené v `_CLIENT_BLOCK` bloky paměti pro běhu C ladění proces výpisu paměti.  
  
 Další informace o použití jiných podporující háku běhové funkce a psaní vlastního klienta definované funkce háku najdete v tématu [ladění zápis funkce háku](/visualstudio/debugger/debug-hook-function-writing).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtGetDumpClient`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_Crtreportblocktype –](../../c-runtime-library/reference/crtreportblocktype.md)   
 [_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md)