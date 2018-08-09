---
title: Module::unregisterwinrtobject – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterWinRTObject method
ms.assetid: 32334aa7-2293-40d2-9a89-4b02e2e31f3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93c804f9e7701ab3bf021902b62ae3f1b414d61c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019076"
---
# <a name="moduleunregisterwinrtobject-method"></a>Module::UnregisterWinRTObject – metoda
Zruší registraci jeden nebo více objektů prostředí Windows Runtime, tak, aby k nim nelze připojit další aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
virtual HRESULT UnregisterWinRTObject(  
   unsigned int,  
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Soubor cookie*  
 Ukazatel na hodnotu, která identifikuje objektu třídy, jehož registrace je zrušené.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)