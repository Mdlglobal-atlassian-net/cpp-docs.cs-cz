---
title: unsupported_feature – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
dev_langs:
- C++
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7472e8fa8932983569ad9e2a9c1fe6cdfc9318b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059677"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature – třída
Výjimka, která je vyvolána při použití nepodporované funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[unsupported_feature – konstruktor](#ctor)|Vytvoří novou instanci třídy `unsupported_feature` výjimky.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## <a name="unsupported_feature__ctor"></a> unsupported_feature – 

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
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
