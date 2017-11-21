---
title: _com_error::_com_error | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::_com_error
dev_langs: C++
helpviewer_keywords: _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 440151fd8b8cd7d28b1e2a9ad951e238ae41dffb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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