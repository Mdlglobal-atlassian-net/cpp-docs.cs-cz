---
title: "__max – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __max
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
- max
- __max
dev_langs: C++
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 585d2a295bedb8b0ba49a893d5089bc682a1debd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="max"></a>__max
Vrátí větší ze dvou hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
type __max(  
   type a,  
   type b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Všechny číselným datovým typem.  
  
 `a, b`  
 Hodnoty všech číselného typu, který se má porovnat.  
  
## <a name="return-value"></a>Návratová hodnota  
 `__max`Vrátí větší argumentů.  
  
## <a name="remarks"></a>Poznámky  
 `__max` Makro porovná dvě hodnoty a vrátí hodnotu typu větší. Argumenty, které může být jakékoli číselný datový typ, podepsané nebo bez znaménka. Argumenty a návratová hodnota musí být stejného datového typu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`__max`|\<stdlib.h >|  
  
## <a name="example"></a>Příklad  
 Další informace, podívejte se na příklad pro [__min –](../../c-runtime-library/reference/min.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [__min](../../c-runtime-library/reference/min.md)