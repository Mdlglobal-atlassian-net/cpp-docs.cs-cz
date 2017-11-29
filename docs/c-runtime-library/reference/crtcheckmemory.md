---
title: "_Crtcheckmemory – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
dev_langs: C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0094c43b7bbe60da1a89d201d40577422b7a889a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory
Potvrdí její integritu bloky paměti přidělené v haldě ladění (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `_CrtCheckMemory` vrátí hodnotu TRUE; jinak hodnota, funkce vrátí hodnotu FALSE.  
  
## <a name="remarks"></a>Poznámky  
 `_CrtCheckMemory` Funkce ověří paměti přidělené správcem haldy ladění ověření základní základní haldy a zkontrolujete každých bloku paměti. Pokud je v haldě základní základní, informace hlavičky ladění nebo přepsat vyrovnávací paměti, chyby nebo paměť nekonzistence `_CrtCheckMemory` generuje sestavy ladicí informace popisující chybu. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání `_CrtCheckMemory` jsou odebrány při předběžném zpracování.  
  
 Chování `_CrtCheckMemory` se dá nastavit podle nastavení pole bit [_crtdbgflag –](../../c-runtime-library/crtdbgflag.md) příznak pomocí [_crtsetdbgflag –](../../c-runtime-library/reference/crtsetdbgflag.md) funkce. Zapnutí **_crtdbg_check_always_df –** bit ON výsledky v poli `_CrtCheckMemory` volané pokaždé, když je požadovaná operace na přidělení paměti. I když tato metoda zpomaluje spuštění, je vhodné pro zachytávání chyb rychle. Zapnutí **_crtdbg_alloc_mem_df –** bit pole OFF příčiny `_CrtCheckMemory` není ověřte halda a okamžitě vrátit **TRUE**.  
  
 Protože funkce vrátí hodnotu **TRUE** nebo **FALSE**, mohla být předána do jednoho z [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra pro vytváření jednoduchých ladění chyba mechanismu pro zpracování. Následující příklad způsobí, že výraz je neplatný. Pokud bylo zjištěno poškození haldy:  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 Další informace o tom, `_CrtCheckMemory` lze použít s další funkce ladění najdete v tématu [funkce vytváření sestav stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Přehled správy paměti a haldy ladění, najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtCheckMemory`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `_CrtCheckMemory`, najdete v části [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_crtdbgflag –](../../c-runtime-library/crtdbgflag.md)   
 [_Crtsetdbgflag –](../../c-runtime-library/reference/crtsetdbgflag.md)