---
title: "invalid_operation – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_operation
- CONCRT/concurrency::invalid_operation
- CONCRT/concurrency::invalid_operation::invalid_operation
dev_langs: C++
helpviewer_keywords: invalid_operation class
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 32053eaadc80a69b2ecdcf8887092ac8fadbdf8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="invalidoperation-class"></a>invalid_operation – třída
Tato třída popisuje výjimka vyvolána v případě, že se provádí na neplatnou operaci, která není popsat přesněji jiný typ výjimky vyvolané Concurrency Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_operation : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_operation](#ctor)|Přetíženo. Vytvoří `invalid_operation` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Různé metody, které throw tato výjimka se obecně dokumentů za jakých okolností bude vyvolají ho.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_operation`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a>invalid_operation 

 Vytvoří `invalid_operation` objektu.  
  
```
explicit _CRTIMP invalid_operation(_In_z_ const char* _Message) throw();

invalid_operation() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)