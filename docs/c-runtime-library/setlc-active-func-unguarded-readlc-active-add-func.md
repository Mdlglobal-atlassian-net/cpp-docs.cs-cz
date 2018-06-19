---
title: ___setlc_active_func ___unguarded_readlc_active_add_func | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 532aac2e47a402ae04ba4d4bf4fcb133c997bd31
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409732"
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
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)