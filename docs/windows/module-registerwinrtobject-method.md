---
title: "Module::registerwinrtobject – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 279a661fae0def63443c9a42d2f290b8d23fa2a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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