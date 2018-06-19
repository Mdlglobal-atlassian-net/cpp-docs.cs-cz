---
title: scheduler_ptr – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 672e4a0dd5f66ab613dde8877915c799d6c4b2f4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686981"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr Structure
Představuje ukazatel plánovače. Tato třída existuje umožňující specifikace sdílené životnost pomocí shared_ptr nebo jen prostý odkaz pomocí nezpracovaná ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_ptr::scheduler_ptr](#ctor)|Přetíženo. Vytvoří ukazatel scheduler z shared_ptr plánovačem|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_ptr::get](#get)|Vrátí nezpracovaná ukazatele do plánovače|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_ptr::Operator – bool](#operator_bool)|Otestovat, zda je ukazatel scheduler jinou hodnotu než null|  
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Chovají jako ukazatel|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `scheduler_ptr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** pplinterface.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="get"></a>  scheduler_ptr::Get – metoda  
 Vrátí nezpracovaná ukazatele do plánovače  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_bool"></a>  scheduler_ptr::Operator – bool   
 Otestovat, zda je ukazatel scheduler jinou hodnotu než null  
  
"" operátor bool() const;
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface – * – operátor -> () const;
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
explicitní scheduler_ptr – (std::shared_ptr < scheduler_interface – > scheduler);

explicitní scheduler_ptr – (_In_opt_ scheduler_interface – * pScheduler);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)
