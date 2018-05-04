---
title: _set_app_type | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
dev_langs:
- C++
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc9b3901cb031a1cc08d911889dc97818cfb5a44
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="setapptype"></a>_set_app_type
Vnitřní funkce, která používá při spuštění CRT říct, zda je aplikace konzolovou aplikaci nebo aplikaci pomocí grafického uživatelského rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    ); 
```  
  
## <a name="parameters"></a>Parametry  
 `appType`  
 Hodnota, která určuje typ aplikace. Možné hodnoty jsou:  
  
|Hodnota|Popis|  
|----------------|-----------------|  
|_crt_unknown_app|Typ neznámé aplikace.|  
|_crt_console_app|Aplikace konzoly (příkazového řádku).|  
|_crt_gui_app|Aplikace s grafickým uživatelským rozhraním (Windows).|  
  
## <a name="remarks"></a>Poznámky  
 Za normálních okolností nepotřebujete volání této funkce. Je součástí C runtime spuštění kódu, který spouští před `main` nazývá ve vaší aplikaci.
 
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|_set_app_type|Process.h|

