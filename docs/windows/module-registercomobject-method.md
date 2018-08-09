---
title: Module::registercomobject – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61ebc6b7bfb0571ba1f2ce1957d916ecb4c790c7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010981"
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject – metoda
Zaregistruje jeden nebo více objektů modelu COM, takže k nim mohli připojit další aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
### <a name="parameters"></a>Parametry  
 *název_serveru*  
 Plně kvalifikovaný název serveru.  
  
 *CLSID*  
 Pole CLSID k registraci.  
  
 *objekty pro vytváření*  
 Pole rozhraní IUnknown objektů tříd, jejichž dostupnost je publikován.  
  
 *Soubory cookie*  
 Po dokončení operace, pole ukazatelů na hodnoty, které identifikují třídu objektů, které jste zaregistrovali. Tyto hodnoty se později použijí zrušit registraci.  
  
 *Počet*  
 Počet CLSID k registraci.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud úspěšné; v opačném případě HRESULT jako je například CO_E_OBJISREG, který označuje důvod operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 Objekty modelu COM jsou registrovány CLSCTX_LOCAL_SERVER enumerátor výčtu CLSCTX.  
  
 Typ připojení k registrované objekty je určená kombinací aktuální *comflag* parametr šablony a REGCLS_SUSPENDED enumerátor výčtu REGCLS.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)