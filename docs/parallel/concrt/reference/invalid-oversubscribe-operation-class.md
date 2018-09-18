---
title: invalid_oversubscribe_operation – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4e1eaf4bfca27ef22af103a5696ca2a34265d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069181"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation – třída
Tato třída popisuje výjimku vyvolána, když `Context::Oversubscribe` metoda je volána `_BeginOversubscription` parametr nastaven na `false` bez předchozího volání `Context::Oversubscribe` metodu s `_BeginOversubscription` parametr nastaven na `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_oversubscribe_operation](#ctor)|Přetíženo. Vytvoří `invalid_oversubscribe_operation` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> invalid_oversubscribe_operation – 

 Vytvoří `invalid_oversubscribe_operation` objektu.  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
