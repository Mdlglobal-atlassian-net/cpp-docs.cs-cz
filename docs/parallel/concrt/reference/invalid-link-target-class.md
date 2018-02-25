---
title: "invalid_link_target – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
dev_langs:
- C++
helpviewer_keywords:
- invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3a4ac6888f22fcedb494865a219fc0dd8e8a98c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="invalidlinktarget-class"></a>invalid_link_target – třída
Tato třída popisuje výjimka vyvolaná při `link_target` je volána metoda blok zasílání zpráv a zasílání zpráv blok nejde připojit k cíli. To může být výsledkem vyšší než počet odkazů, které je povoleno zasílání zpráv bloku nebo při pokusu o odkaz na konkrétní cíl dvakrát pro stejný zdroj.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class invalid_link_target : public std::exception;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_link_target](#ctor)|Přetíženo. Vytvoří `invalid_link_target` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `invalid_link_target`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> invalid_link_target 

 Vytvoří `invalid_link_target` objektu.  
  
```
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popisný zpráva o chybě.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md)



