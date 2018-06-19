---
title: Activationfactory::QueryInterface – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 2a9b71aa-61c0-43f7-aa35-00f0ee0af031
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d93a2f61e92172c94fef2406fc6caa2de71ab8e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854506"
---
# <a name="activationfactoryqueryinterface-method"></a>ActivationFactory::QueryInterface – metoda
Načte ukazatele k zadanému rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   QueryInterface  
)(REFIID riid, _Deref_out_ void **ppvObject);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identifikátor rozhraní.  
  
 `ppvObject`  
 Po dokončení této operace, ukazatel na rozhraní určený parametrem `riid`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT popisující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ActivationFactory – třída](../windows/activationfactory-class.md)