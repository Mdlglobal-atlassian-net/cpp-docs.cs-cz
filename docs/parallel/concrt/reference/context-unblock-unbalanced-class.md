---
title: context_unblock_unbalanced – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs:
- C++
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c964701f9a26c655bbb9529a112f036c7c9f0bf5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced – třída
Tato třída popisuje výjimka vyvolaná při volání `Block` a `Unblock` metody `Context` objekt nejsou spárovány správně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class context_unblock_unbalanced : public std::exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[context_unblock_unbalanced](#ctor)|Přetíženo. Vytvoří `context_unblock_unbalanced` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Volání `Block` a `Unblock` metody `Context` objekt musí vždy správně spárovat. Concurrency Runtime umožňuje operace, provést v buď pořadí. Například volání `Block` může následovat volání `Unblock`, nebo naopak. Tato výjimka by vyvolat, je-li například dva volá, aby se `Unblock` metoda byly provedeny v řádku, na `Context` objekt, který nebyl blokován.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> context_unblock_unbalanced 

 Vytvoří `context_unblock_unbalanced` objektu.  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
