---
title: Activationfactory::getruntimeclassname – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: edc4658ebf0519ef9d1792d62b303f423e658835
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643066"
---
# <a name="activationfactorygetruntimeclassname-method"></a>ActivationFactory::GetRuntimeClassName – metoda
Získá název třídy runtime objektu, který aktuální **activationfactory –** vytvoří instanci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
### <a name="parameters"></a>Parametry  
 *runtimeName*  
 Když tato operace dokončí, popisovač pro řetězec, který obsahuje název třídy runtime objektu, který aktuální **activationfactory –** vytvoří instanci.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ActivationFactory – třída](../windows/activationfactory-class.md)