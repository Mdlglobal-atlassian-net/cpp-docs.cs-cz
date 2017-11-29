---
title: "scheduler_resource_allocation_error – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::scheduler_resource_allocation_error
- CONCRT/concurrency::scheduler_resource_allocation_error::get_error_code
dev_langs: C++
helpviewer_keywords: scheduler_resource_allocation_error class
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 334712def2fbd458b648b02cbfab05e202cc0e1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="schedulerresourceallocationerror-class"></a>scheduler_resource_allocation_error – třída
Tato třída popisuje výjimce z důvodu selhání získat prostředek kritické v Concurrency Runtime.  
  
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
|[get_error_code –](#get_error_code)|Vrátí kód chyby, který způsobil výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato výjimka se obvykle vyvolá, když selže volání operačního systému z v Concurrency Runtime. Kód chyby, která by za normálních okolností vrácená z volání metody Win32 `GetLastError` jsou převedeny na hodnotu typu `HRESULT` a můžete načíst pomocí `get_error_code` metoda.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="get_error_code"></a>get_error_code – 

 Vrátí kód chyby, který způsobil výjimku.  
  
```
HRESULT get_error_code() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `HRESULT` Hodnotu chyby, který způsobil výjimku.  
  
##  <a name="ctor"></a>scheduler_resource_allocation_error 

 Vytvoří `scheduler_resource_allocation_error` objektu.  
  
```
scheduler_resource_allocation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_resource_allocation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
 `_Hresult`  
 `HRESULT` Hodnotu chyby, který způsobil výjimku.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)