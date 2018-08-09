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
ms.openlocfilehash: 240ab47099b9e97e9a6bb794083858fe042605d2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018692"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject – metoda
Zruší jeden nebo více objektů modelu COM, registraci což zabrání aplikacím bránily v připojení k nim.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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