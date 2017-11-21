---
title: __RTDynamicCast | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords: __RTDynamicCast
dev_langs: C++
helpviewer_keywords: __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b648d2f0f63a13451d5625c99e5bf614c8402017
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rtdynamiccast"></a>__RTDynamicCast
Implementace modulu runtime [dynamic_cast](../cpp/dynamic-cast-operator.md) operátor.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
PVOID __RTDynamicCast (  
   PVOID inptr,   
   LONG VfDelta,  
   PVOID SrcType,  
   PVOID TargetType,   
   BOOL isReference  
   ) throw(...)  
```  
  
#### <a name="parameters"></a>Parametry  
 `inptr`  
 Ukazatel na polymorfní objekt.  
  
 `VfDelta`  
 Posun virtuální funkce ukazatele v objektu.  
  
 `SrcType`  
 Statický typ objektu, na kterou odkazuje `inptr` parametr.  
  
 `TargetType`  
 Zamýšlený výsledek přetypování.  
  
 `isReference`  
 `true`Pokud vstup je odkaz; `false` Pokud vstup je ukazatel.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na příslušnou dílčí objekt, v případě úspěšného; jinak hodnota NULL.  
  
## <a name="exceptions"></a>Výjimky  
 `bad_cast()`Pokud vstup `dynamic_cast<>` je odkaz, přetypování selže.  
  
## <a name="remarks"></a>Poznámky  
 Převede `inptr` na objekt typu `TargetType`. Typ `inptr` musí být ukazatel, pokud `TargetType` ukazatel nebo hodnotu l `TargetType` je odkaz. `TargetType`musí být ukazatel nebo odkaz na typ dříve definované třídy, nebo ukazatel na void.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__RTDynamicCast|rtti.h|