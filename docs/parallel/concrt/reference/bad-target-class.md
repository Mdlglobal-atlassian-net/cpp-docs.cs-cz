---
title: "bad_target – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
dev_langs:
- C++
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 178d8519516790be3cdb2d9178cc8ffdf144ea23
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="badtarget-class"></a>bad_target – třída
Tato třída popisuje výjimka vyvolaná při zasílání zpráv blok je zadána ukazatel cíl, který je neplatný pro prováděnou operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class bad_target : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[bad_target](#ctor)|Přetíženo. Vytvoří `bad_target` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato výjimka je obvykle vyvolána z důvodů, jako je například cíl pokusu využívat zprávu, která je vyhrazena pro jiný cíl nebo vydání rezervace, který nemá.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `bad_target`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> bad_target 

 Vytvoří `bad_target` objektu.  
  
```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md)



