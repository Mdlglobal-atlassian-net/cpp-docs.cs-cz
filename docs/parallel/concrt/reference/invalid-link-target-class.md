---
title: invalid_link_target – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2120f274dd783da00a43106338476c43cc0a9dad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021743"
---
# <a name="invalidlinktarget-class"></a>invalid_link_target – třída
Tato třída popisuje výjimku vyvolána, když `link_target` je volána metoda blok zpráv a blok zpráv se nejde připojit k cíli. To může být vyšší než počet odkazů, které je povoleno blok zpráv nebo pokus o odkaz konkrétní cílovou dvakrát ke stejnému zdroji.  
  
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
  
##  <a name="ctor"></a> invalid_link_target – 

 Vytvoří `invalid_link_target` objektu.  
  
```
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popisná zpráva chyby.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [Asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md)



