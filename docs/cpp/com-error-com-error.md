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
ms.openlocfilehash: ec16faa9881fc1c69dca5f8f39b8797cf0fcff0d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947600"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Specifické pro Microsoft**  
  
 Vytvoří `_com_error` objektu.  
  
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
 Konstruktor zavolá funkci AddRef pro nenulovým `IErrorInfo` rozhraní. Tím lze zajistit správné počítání referencí v obvyklém případě, kdy je vlastnictví rozhraní předáváno objektu `_com_error`, například:  
  
```cpp 
throw _com_error(hr, perrinfo);  
```  
  
 Pokud nechcete, aby kód převáděl vlastnictví `_com_error` objektu a `AddRef` vyžadován posun `Release` v `_com_error` destruktor, sestavte objekt takto:  
  
```cpp 
_com_error err(hr, perrinfo, true);  
```  
  
 *který*  
 Existující objekt `_com_error`.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor vytvoří nový objekt dle HRESULT a volitelné `IErrorInfo` objektu. Objekt IErrorInfo vytvoří kopii existujícího objektu `_com_error`.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_com_error – třída](../cpp/com-error-class.md)