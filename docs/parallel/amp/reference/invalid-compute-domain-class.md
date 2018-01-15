---
title: "invalid_compute_domain – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
dev_langs: C++
helpviewer_keywords: invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9dc142b921efb6b52fd5b5ce7a89432b4727951c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain – třída
Výjimka, která se vyvolá, když modul runtime nelze spustit jádra pomocí zadané v doméně výpočetní [parallel_for_each –](concurrency-namespace-functions-amp.md#parallel_for_each) volání lokality.  

  
## <a name="syntax"></a>Syntaxe  
  
```  
class invalid_compute_domain : public runtime_exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[invalid_compute_domain – konstruktor](#ctor)|Inicializuje novou instanci třídy `invalid_compute_domain` třídy.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `runtime_exception`  
  
 `invalid_compute_domain`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  

## <a name="ctor"></a>invalid_compute_domain 

Inicializuje novou instanci třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit invalid_compute_domain(  
    const char * _Message ) throw();  
  
invalid_compute_domain() throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popis chyby.  
  
### <a name="return-value"></a>Návratová hodnota  
 Instance `invalid_compute_domain` – třída  
    
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
