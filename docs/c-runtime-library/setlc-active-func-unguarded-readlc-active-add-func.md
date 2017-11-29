---
title: ___setlc_active_func ___unguarded_readlc_active_add_func | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
dev_langs: C++
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a1746d597613bf76bdbf8c38ff3487b4d0c18fc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func ___unguarded_readlc_active_add_func
ZASTARALÉ. CRT exportuje tyto interní funkce pouze pro zachování kompatibility binární.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int ___setlc_active_func(void);  
int * ___unguarded_readlc_active_add_func(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota vrácená není důležité.  
  
## <a name="remarks"></a>Poznámky  
 I když interní funkce CRT `___setlc_active_func` a `___unguarded_readlc_active_add_func` jsou zastaralé a už nebude používat, jsou exportované sadou knihovny CRT zachování kompatibility binární. Původní účel `___setlc_active_func` bylo vrátí počet aktuálně aktivních volání `setlocale` funkce. Původní účel `___unguarded_readlc_active_add_func` bylo vrátí počet funkcí, které odkazuje národní prostředí bez blokování ho.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|žádná|  
  
## <a name="see-also"></a>Viz také  
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)