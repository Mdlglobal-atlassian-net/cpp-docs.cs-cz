---
title: "cancellation_token_registration – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
dev_langs: C++
helpviewer_keywords: cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2d80255803c4d2ca2aec05af8115ac887f7258b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration – třída
`cancellation_token_registration` Třída reprezentuje zpětné volání oznámení z `cancellation_token`. Když `register` metodu `cancellation_token` se používá k přijetí oznámení o zrušení v případech, `cancellation_token_registration` jako popisovač pro zpětné volání tak, aby volající požadovat zpětného volání konkrétní už být provedeny prostřednictvím použití sevrátíobjekt`deregister` metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class cancellation_token_registration;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[cancellation_token_registration](#ctor)||  
|[~ cancellation_token_registration – destruktor](#dtor)||  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Operator! =](#operator_neq)||  
|[operátor =](#operator_eq)||  
|[Operator ==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `cancellation_token_registration`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** pplcancellation_token.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a>~ cancellation_token_registration 

```
~cancellation_token_registration();
```  
  
##  <a name="ctor"></a>cancellation_token_registration 

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
##  <a name="operator_neq"></a>Operator! = 

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq"></a>operátor = 

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq_eq"></a>Operator == 

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Návratová hodnota  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)