---
title: Zpracování makra výjimek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs:
- C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05ee381aa792c252fc9b80107d25e15e7d1ecfca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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

##  <a name="_atlcatch"></a>  _ATLCATCH  
 Příkazy se budou zpracovávat chyby, ke kterým dochází v přidruženém `_ATLTRY`.  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>Parametry  
 *e*  
 Výjimka k zachycení.  
  
### <a name="remarks"></a>Poznámky  
 Používá ve spojení s `_ATLTRY`. Přeloží na C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování daný typ výjimky jazyka C++.  
  
##  <a name="_atlcatchall"></a>  _ATLCATCHALL  
 Příkazy se budou zpracovávat chyby, ke kterým dochází v přidruženém `_ATLTRY`.  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>Poznámky  
 Používá ve spojení s `_ATLTRY`. Přeloží na C++ [catch(...) ](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování všech typů výjimky jazyka C++.  
  
##  <a name="_atltry"></a>  _ATLTRY  
 Označí chráněného kódu části, kde pravděpodobně dojde k chybě.  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>Poznámky  
 Používá ve spojení s [_ATLCATCH](#_atlcatch) nebo [_ATLCATCHALL](#_atlcatchall). Přeloží na C++ symbol [zkuste](../../cpp/try-throw-and-catch-statements-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
