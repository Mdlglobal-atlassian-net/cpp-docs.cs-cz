---
title: __set_app_type | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __set_app_type
- _set_app_type
apilocation:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __set_app_type
dev_langs:
- C++
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 854873987cd83b89efc5c9006c1e091023c91226
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389059"
---
# <a name="setapptype"></a>__set_app_type
Nastaví aktuální typ aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __set_app_type (  
   int at  
   )  
```  
  
#### <a name="parameters"></a>Parametry  
 `at`  
 Hodnota, která určuje typ aplikace. Možné hodnoty jsou:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|_UNKNOWN_APP|Typ neznámé aplikace.|  
|_CONSOLE_APP|Aplikace konzoly (příkazového řádku).|  
|_GUI_APP|Aplikace s grafickým uživatelským rozhraním (Windows).|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__set_app_type|internal.h|