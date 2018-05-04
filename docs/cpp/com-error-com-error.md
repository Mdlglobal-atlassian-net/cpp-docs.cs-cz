---
title: _com_error::_com_error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d26239f6edf98e90f9d4d773d654025da410a97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Konkrétní Microsoft**  
  
 Vytvoří `_com_error` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      _com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false  
) throw( );  
_com_error(  
   const _com_error& that   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `hr`  
 Informace `HRESULT`.  
  
 `perrinfo`  
 **IErrorInfo** objektu.  
  
 **BOOL fAddRef = false**  
 Způsobí, že konstruktor k volání addref – na hodnotu null **IErrorInfo** rozhraní. Tím lze zajistit správné počítání referencí v obvyklém případě, kdy je vlastnictví rozhraní předáváno objektu `_com_error`, například:  
  
```  
throw _com_error(hr, perrinfo);  
```  
  
 Pokud nechcete, aby váš kód převést vlastnictví na `_com_error` objekt a `AddRef` je potřeba posun **verze** v `_com_error` destruktor, vytvořit objekt následujícím způsobem:  
  
```  
_com_error err(hr, perrinfo, true);  
```  
  
 `that`  
 Existující objekt `_com_error`.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktoru vytvoří nový objekt zadané `HRESULT` a volitelné **IErrorInfo** objektu. Objekt IErrorInfo vytvoří kopii existujícího objektu `_com_error`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)