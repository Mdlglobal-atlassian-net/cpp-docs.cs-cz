---
title: _com_error::_com_error | Dokumentace Microsoftu
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
ms.openlocfilehash: c1389635c3ef026e8b3a7dfe13976cca58a15a82
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406715"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Specifické pro Microsoft**  
  
 Vytvoří **_com_error** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false) throw( );  

_com_error( const _com_error& that ) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *hr*  
 Informace o HRESULT.  
  
 *perrinfo*  
 `IErrorInfo` objekt.  
  
 `bool fAddRef=false`  
 Konstruktor zavolá funkci AddRef pro nenulovým `IErrorInfo` rozhraní. To umožňuje správné počítání referencí v obvyklém případě, kdy je vlastnictví rozhraní předána do **_com_error** objektů, jako například:  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 Pokud nechcete, aby kód převáděl vlastnictví **_com_error –** objektu a `AddRef` vyžadován posun `Release` v **_com_error –** destruktor, vytvořit jako objekt následující:  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *který*  
 Existující **_com_error** objektu.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor vytvoří nový objekt dle HRESULT a volitelné `IErrorInfo` objektu. Objekt IErrorInfo vytvoří kopii stávající **_com_error** objektu.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [_com_error – třída](../cpp/com-error-class.md)