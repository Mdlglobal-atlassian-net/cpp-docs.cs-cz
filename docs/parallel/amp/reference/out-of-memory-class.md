---
title: out_of_memory – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
dev_langs:
- C++
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ab3285e0b37b8af93803a1a2752e25b6d91ab2f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695292"
---
# <a name="outofmemory-class"></a>out_of_memory – třída
Výjimka, která se vyvolá, když metoda selže z důvodu nedostatku paměti systému nebo zařízení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[out_of_memory – konstruktor](#ctor)|Inicializuje novou instanci třídy `out_of_memory` třídy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  
## <a name="ctor"></a> out_of_memory 

 Inicializuje novou instanci třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
explicit out_of_memory(  
    const char * _Message ) throw();  
  
out_of_memory () throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popis chyby.  
  
### <a name="return-value"></a>Návratová hodnota  
 Novou instanci třídy `out_of_memory` třídy.  
  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
