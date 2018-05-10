---
title: runtime_exception – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff10cb3958ffa82e3ef2bb70d8370d1a52c4a929
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="runtimeexception-class"></a>runtime_exception – třída
Základní typ pro výjimky v knihovně C++ Accelerated masivní paralelismus (AMP).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
class runtime_exception : public std::exception;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[runtime_exception – konstruktor](#ctor)|Inicializuje novou instanci třídy `runtime_exception` třídy.|  
|[~runtime_exception Destructor](#dtor)|Zničí `runtime_exception` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_error_code](#runtime_exception__get_error_code)|Vrátí kód chyby, který způsobil výjimku.|  

  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `runtime_exception` objekt s touto.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `exception`  
  
 `runtime_exception`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amprt.h  
  
 **Namespace:** souběžnosti  

## <a name="runtime_exception__ctor"></a>  runtime_exception – konstruktor  
Inicializuje novou instanci třídy.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
runtime_exception(  
    const char * _Message,  
    HRESULT _Hresult ) throw();  
  
explicit runtime_exception(  
    HRESULT _Hresult ) throw();  
  
runtime_exception(  
    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Popis chyby, který způsobil výjimku.  
  
 `_Hresult`  
 HRESULT chyby, který způsobil výjimku.  
  
 `_Other`  
 `runtime_exception` Objekt, který chcete kopírovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 `runtime_exception` Objektu.  

## <a name="dtor"></a>  ~ runtime_exception – destruktor  
Zničí objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
virtual ~runtime_exception() throw();  
```  
  
## <a name="runtime_exception__get_error_code"></a>  get_error_code –   
Vrátí kód chyby, který způsobil výjimku.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_error_code() const throw();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 HRESULT chyby, který způsobil výjimku.  
  
## <a name="runtime_exception__operator_eq"></a>  operátor =   
  Zkopíruje obsah zadaného `runtime_exception` objekt s touto.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
runtime_exception & operator= (    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `runtime_exception` Objekt, který chcete kopírovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `runtime_exception` objektu.  
  

  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
