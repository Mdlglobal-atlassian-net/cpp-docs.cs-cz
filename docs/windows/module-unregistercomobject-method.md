---
title: Module::unregistercomobject – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c19e7b5388438b8c3c2359672360e4a2ee3001a3
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602627"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject – metoda
Zruší jeden nebo více objektů modelu COM, registraci což zabrání aplikacím bránily v připojení k nim.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
### <a name="parameters"></a>Parametry  
 *název_serveru*  
 (Nepoužívané)  
  
 *Soubory cookie*  
 Pole ukazatelů na hodnoty, které identifikují objekty třídy pro odstranění registrace. Pole byl vytvořen [registercomobject –](../windows/module-registercomobject-method.md) metody.  
  
 *Počet*  
 Počet tříd se zrušit registraci.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je tato operace úspěšná; S_OK v opačném případě chybu HRESULT, který označuje důvod operace se nezdařila.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)