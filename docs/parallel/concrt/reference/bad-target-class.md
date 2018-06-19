---
title: bad_target – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be10e5e4105dd16a68ad2854538d6181e90bfbe9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705338"
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



