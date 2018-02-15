---
title: "_Crtsetdumpclient – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb8a62dc903b7bb0684d3fffcde8a677200d665d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient
Nainstaluje funkce definované aplikací pro výpis `_CLIENT_BLOCK` zadejte bloky paměti (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dumpClient`  
 Nové funkce výpisu paměti definované klienta připojí do proces výpisu paměti běhové ladění C.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí dříve definovaném klientský blok dump funkce.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtSetDumpClient` Funkce umožňuje aplikaci připojit svůj vlastní funkce k výpisu objekty uložené v `_CLIENT_BLOCK` bloky paměti do běhu C ladění proces výpisu paměti. V důsledku toho se pokaždé, když a ladění dump funkce, jako [_crtmemdumpallobjectssince –](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) nebo [_crtdumpmemoryleaks –](../../c-runtime-library/reference/crtdumpmemoryleaks.md) výpisy paměti `_CLIENT_BLOCK` bloku paměti aplikace výpisu funkce je volána také. `_CrtSetDumpClient` umožní aplikaci snadno pro zjišťování nevracení paměti a ověřování nebo generování sestav obsah dat uložených v `_CLIENT_BLOCK` bloky. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtSetDumpClient` jsou odebrány při předběžném zpracování.  
  
 `_CrtSetDumpClient` Funkce nainstaluje nové funkce definované aplikací výpisu zadaný v `dumpClient` a vrátí funkce dříve definovaném výpis. Příklad funkce výpisu bloku klienta vypadá takto:  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 `userPortion` Argument je ukazatel na začátku části data uživatele bloku paměti a `blockSize` Určuje velikost paměti přidělené blokovat v bajtech. Funkce klienta bloku výpisu musí vracet `void`. Ukazatel na funkci výpisu klienta, která je předána `_CrtSetDumpClient` je typu `_CRT_DUMP_CLIENT`, jak jsou definovány v Crtdbg.h:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 Další informace o funkcích, které působí na `_CLIENT_BLOCK` zadejte bloky paměti najdete v tématu [funkce háku bloku klienta](/visualstudio/debugger/client-block-hook-functions). [_Crtreportblocktype –](../../c-runtime-library/reference/crtreportblocktype.md) funkce lze použít k vrácení informací o typy bloku a podtypech.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtSetDumpClient`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)