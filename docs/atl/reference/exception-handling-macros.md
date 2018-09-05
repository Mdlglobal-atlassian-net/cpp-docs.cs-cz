---
title: Makra pro zpracování výjimek | Dokumentace Microsoftu
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
ms.openlocfilehash: b503e36dfe04eaa3180809033187957ff8d970a0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766812"
---
# <a name="exception-handling-macros"></a>Makra zpracování výjimek

Tato makra poskytovat podporu pro zpracování výjimek.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.|
|[_ATLCATCHALL](#_atlcatchall)|Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.|
|[_ATLTRY](#_atltry)|Označí strážených kód části, kde může případně dojít k chybě.|

## <a name="requirements"></a>Požadavky:

**Záhlaví:** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parametry

*e*  
Výjimka pro zachycení.

### <a name="remarks"></a>Poznámky

Použít ve spojení s `_ATLTRY`. Přeloží na C++ [catch (catlexception – e)](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování daného typu výjimky jazyka C++.

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

Příkazů pro zpracování chyb, ke kterým dochází v přidruženém `_ATLTRY`.

```
_ATLCATCHALL
```

### <a name="remarks"></a>Poznámky

Použít ve spojení s `_ATLTRY`. Přeloží na C++ [catch(...) ](../../cpp/try-throw-and-catch-statements-cpp.md) pro zpracování všech druhů výjimky jazyka C++.

##  <a name="_atltry"></a>  _ATLTRY

Označí strážených kód části, kde může případně dojít k chybě.

```
_ATLTRY
```

### <a name="remarks"></a>Poznámky

Použít ve spojení s [_ATLCATCH](#_atlcatch) nebo [_ATLCATCHALL](#_atlcatchall). Přeloží na symbolu C++ [zkuste](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
