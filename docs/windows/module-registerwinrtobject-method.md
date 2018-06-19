---
title: Module::registerwinrtobject – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 097bf70ebd280d9494ff70ea1d80f53615f3d898
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874951"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject – metoda
Jeden nebo více objektů prostředí Windows Runtime zaregistruje, takže k nim můžou připojit jiné aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RegisterWinRTObject(const wchar_t* serverName,  
   wchar_t** activatableClassIds,  
   WINRT_REGISTRATION_COOKIE* cookie,  
   unsigned int count)  
```  
  
#### <a name="parameters"></a>Parametry  
 `serverName`  
 Název, který určuje podmnožinu objektů vliv na tuto operaci.  
  
 `activatableClassIds`  
 Pole activatable CLSID k registraci.  
  
 `cookie`  
 Hodnota, která identifikuje objekty tříd, které byly zaregistrovány. Tato hodnota se používá novější zrušení registrace.  
  
 `count`  
 Počet objektů, které chcete zaregistrovat.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném chybu HRESULT například CO_E_OBJISREG, která určuje, z důvodu operace se nezdařila.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)