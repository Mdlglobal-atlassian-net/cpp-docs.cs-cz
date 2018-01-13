---
title: "_endthread –, _endthreadex | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _endthread
- _endthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _endthread
- endthreadex
- _endthreadex
- endthread
dev_langs: C++
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5abe2f0aa2f62048fefb2f79614e018fbdb51e08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="endthread-endthreadex"></a>_endthread, _endthreadex
Ukončí podprocesu. `_endthread` ukončuje podproces, který byl vytvořený `_beginthread` a `_endthreadex` ukončuje podproces, který byl vytvořený `_beginthreadex`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _endthread( void );  
void _endthreadex(   
   unsigned retval   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `retval`  
 Přístup z více vláken ukončovací kód.  
  
## <a name="remarks"></a>Poznámky  
 Můžete volat `_endthread` nebo `_endthreadex` explicitně k ukončení vlákna; však `_endthread` nebo `_endthreadex` při vlákno vrátí z rutiny předány jako parametr, který se nazývá automaticky `_beginthread` nebo `_beginthreadex`. Ukončení vlákna pomocí volání `endthread` nebo `_endthreadex` pomáhá zajistit, aby správné obnovení prostředky přidělené pro vlákno.  
  
> [!NOTE]
>  Pro spustitelný soubor, propojený s Libcmt.lib, nevolejte Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) rozhraní API; to brání spuštění systému opětovného získání přidělené prostředky. `_endthread`a `_endthreadex` uvolnit prostředky přidělené vláken a pak zavolají `ExitThread`.  
  
 `_endthread`automaticky zavře popisovač podprocesu. (Toto chování se liší od Win32 `ExitThread` rozhraní API.) Proto při použití `_beginthread` a `_endthread`, popisovač podprocesu explicitně nezavírejte voláním Win32 [funkce CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) rozhraní API.  
  
 Jako Win32 `ExitThread` rozhraní API, `_endthreadex` nezavře popisovač podprocesu. Proto při použití `_beginthreadex` a `_endthreadex`, je třeba nejprve zavřít popisovač podprocesu voláním Win32 `CloseHandle` rozhraní API.  
  
> [!NOTE]
>  `_endthread`a `_endthreadex` způsobit C++ destruktory čekající na vyřízení ve vláknu není, která se má volat.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_endthread`|\<Process.h >|  
|`_endthreadex`|\<Process.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Vícevláknové verzích [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)