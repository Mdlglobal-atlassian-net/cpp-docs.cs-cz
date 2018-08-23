---
title: scheduler_ptr – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 99c2ed2f8446b94d606c907f4d030c417e21fc01
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465944"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr Structure
Představuje ukazatel na Plánovač. Tato třída existuje pro povolení specifikace sdílené životnosti pomocí shared_ptr nebo jen prostým odkazem pomocí nezpracovaného ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_ptr::scheduler_ptr](#ctor)|Přetíženo. Vytvoří ukazatel plánovače z shared_ptr do plánovače|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_ptr::get](#get)|Vrátí ukazatel raw pro Plánovač|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[scheduler_ptr::Operator bool](#operator_bool)|Otestujte, zda ukazatel plánovače nemá hodnotu null|  
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Chovají se jako ukazatel|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `scheduler_ptr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** pplinterface.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="get"></a>  scheduler_ptr::Get – metoda  
 Vrátí ukazatel raw pro Plánovač  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_bool"></a>  scheduler_ptr::Operator bool   
 Otestujte, zda ukazatel plánovače nemá hodnotu null  
  
'''operator bool() const;
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface – * – operátor -> const;)
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
scheduler_ptr – explicitní (std::shared_ptr < scheduler_interface – > Plánovač);

scheduler_ptr – explicitní (_In_opt_ pScheduler scheduler_interface – *);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)
