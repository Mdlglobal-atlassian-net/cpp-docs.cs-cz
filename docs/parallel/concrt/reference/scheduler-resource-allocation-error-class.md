---
title: scheduler_resource_allocation_error – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ede37cec7b654c2d5ead32f117e4fe76f28fa60
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101693"
---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error – třída
Tato třída popisuje výjimku vyvolána, protože se nepodařilo získat důležitých prostředků v modulu Runtime souběžnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class scheduler_resource_allocation_error : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_resource_allocation_error](#ctor)|Přetíženo. Vytvoří `scheduler_resource_allocation_error` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_error_code](#get_error_code)|Vrátí kód chyby, který způsobil výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Toto se obvykle výjimka při volání do operačního systému z v rámci modulu Runtime souběžnosti selže. Kód chyby, která by obvykle vrácená z volání metody Win32 `GetLastError` je převedena na hodnotu typu `HRESULT` a je možné načíst pomocí `get_error_code` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="get_error_code"></a> get_error_code – 

 Vrátí kód chyby, který způsobil výjimku.  
  
```
HRESULT get_error_code() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `HRESULT` Hodnotou chyby, který způsobil výjimku.  
  
##  <a name="ctor"></a> scheduler_resource_allocation_error – 

 Vytvoří `scheduler_resource_allocation_error` objektu.  
  
```
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
*_Hresult*<br/>
`HRESULT` Hodnotou chyby, který způsobil výjimku.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
