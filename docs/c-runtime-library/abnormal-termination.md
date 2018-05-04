---
title: _abnormal_termination | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
dev_langs:
- C++
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f70520b60ccfaf1af5b223bcb4ea1a90639aa484
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="abnormaltermination"></a>_abnormal_termination
Určuje, zda `__finally` blokovat z [try-finally – příkaz](../cpp/try-finally-statement.md) se zadá, když systému provádí vnitřní seznam obslužné rutiny ukončení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
int   _abnormal_termination(  
   );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je systém *unwinding* zásobníku, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Toto je interní funkce používat ke správě unwinding výjimky a není určená k volání přímo z uživatelského kódu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|_abnormal_termination|excpt.h|  
  
## <a name="see-also"></a>Viz také  
 [try-finally – příkaz](../cpp/try-finally-statement.md)