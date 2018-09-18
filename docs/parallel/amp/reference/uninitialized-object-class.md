---
title: uninitialized_object – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
dev_langs:
- C++
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 821f3c25d195a2c92ac04fdf5f9e5a59b493c257
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113835"
---
# <a name="uninitializedobject-class"></a>uninitialized_object – třída
Výjimka, která je vyvolána při použití neinicializovaného objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class uninitialized_object : public runtime_exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[uninitialized_object – konstruktor](#ctor)|Inicializuje novou instanci třídy `uninitialized_object` třídy.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  
## <a name="uninitialized_object__ctor"></a> unsupported_feature – 

Sestaví novou instanci výjimky unsupported_feature.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>Parametry  
*_TEXT*<br/>
Popis chyby.  
  
### <a name="return-value"></a>Návratová hodnota  
 `unsupported_feature` Objektu. 

## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
