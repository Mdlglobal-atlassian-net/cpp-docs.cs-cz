---
title: "accelerator_view_removed – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs: C++
helpviewer_keywords: AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68b770acd41956ec255718ee2e2db1c5ee556b9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed – třída
Výjimka, která se vyvolá, když je základní volání rozhraní DirectX nezdaří z důvodu vypršení časového limitu Windows mechanismus detekce a obnovení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[accelerator_view_removed – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator_view_removed` třídy.|  

### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_view_removed_reason](#get_view_removed_reason)|Vrátí kód chyby HRESULT určující příčinu `accelerator_view` odebrání objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  

## <a name="ctor"></a>accelerator_view_removed 

Inicializuje novou instanci třídy [accelerator_view_removed](accelerator-view-removed-class.md) třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
explicit accelerator_view_removed(  
    const char * _Message,  
    HRESULT _View_removed_reason ) throw();  
  
explicit accelerator_view_removed(  
    HRESULT _View_removed_reason ) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popis chyby.  
  
 `_View_removed_reason`  
 Chybový kód HRESULT určující příčinu odebrání `accelerator_view` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Novou instanci třídy accelerator_view_removed.  
  
## <a name="get_view_removed_reason_method"></a>get_view_removed_reason 

Vrátí kód chyby HRESULT určující příčinu `accelerator_view` odebrání objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
