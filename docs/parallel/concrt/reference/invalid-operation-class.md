---
title: invalid_operation – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c189649447b318a651957c82b8cfab8cd11fb60a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054828"
---
# <a name="invalidoperation-class"></a>invalid_operation – třída
Tato třída popisuje výjimku vyvolanou při provádění neplatné operace, která není přesněji popsána jako jiný typ výjimky vyvolané modulem Runtime souběžnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_operation : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_operation –](#ctor)|Přetíženo. Vytvoří `invalid_operation` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Různé metody, které vyvolávají tuto výjimku, většinou dokumentují za jakých okolností se vyvolá ji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_operation`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> invalid_operation – 

 Vytvoří `invalid_operation` objektu.  
  
```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
