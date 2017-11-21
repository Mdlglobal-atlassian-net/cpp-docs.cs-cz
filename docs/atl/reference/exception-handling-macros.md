---
title: "Zpracování makra výjimek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs: C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 906f6d499da04a6bee9da18dbbb6ad4b463c8fa6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exception-handling-macros"></a>Makra zpracování výjimek
Tyto makra poskytuje podporu pro zpracování výjimek.  
  
|||  
|-|-|  
|[_ATLCATCH](#_atlcatch)|Příkazy se budou zpracovávat chyby, ke kterým dochází v přidruženém `_ATLTRY`.|  
|[_ATLCATCHALL](#_atlcatchall)|Příkazy se budou zpracovávat chyby, ke kterým dochází v přidruženém `_ATLTRY`.|  
|[_ATLTRY](#_atltry)|Označí chráněného kódu části, kde pravděpodobně dojde k chybě.|  
  
## <a name="requirements"></a>Požadavky:
**Záhlaví:** atldef.h

##  <a name="_atlcatch"></a>_ATLCATCH  
 Příkazy se budou zpracovávat chyby, ke kterým dochází v přidruženém `_ATLTRY`.  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>Parametry  
 *e*  
 Výjimka k zachycení.  
  
### <a name="remarks"></a>Poznámky  
 Používá ve spojení s `_ATLTRY`. Přeloží na C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování daný typ výjimky jazyka C++.  
  
##  <a name="_atlcatchall"></a>_ATLCATCHALL  
 Příkazy se budou zpracovávat chyby, ke kterým dochází v přidruženém `_ATLTRY`.  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>Poznámky  
 Používá ve spojení s `_ATLTRY`. Přeloží na C++ [catch(...) ](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování všech typů výjimky jazyka C++.  
  
##  <a name="_atltry"></a>_ATLTRY  
 Označí chráněného kódu části, kde pravděpodobně dojde k chybě.  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>Poznámky  
 Používá ve spojení s [_ATLCATCH](#_atlcatch) nebo [_ATLCATCHALL](#_atlcatchall). Přeloží na C++ symbol [zkuste](../../cpp/try-throw-and-catch-statements-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
