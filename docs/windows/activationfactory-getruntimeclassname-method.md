---
title: Activationfactory::getruntimeclassname – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
dev_langs:
- C++
helpviewer_keywords:
- GetRuntimeClassName method
ms.assetid: 74e34f0a-9c51-4b40-89f5-45c6c5886ece
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6db270c88b4335be48016ff2b8bdcf2b5e3951cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="activationfactorygetruntimeclassname-method"></a>ActivationFactory::GetRuntimeClassName – metoda
Získá název modulu runtime třídy objektu, který vytvoří instanci aktuální ActivationFactory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtimeName`  
 Když tato operace dokončí, popisovač pro řetězec, který obsahuje název modulu runtime třídy objektu, který vytvoří instanci aktuální ActivationFactory.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT popisující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ActivationFactory – třída](../windows/activationfactory-class.md)