---
title: Module::registercomobject – metoda | Microsoft Docs
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
ms.openlocfilehash: c002dd64049006c8ee74c709c585a3a9d0f253a5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject – metoda
Zaregistruje jeden nebo více objektů COM, můžete k nim připojit jiné aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `serverName`  
 Plně kvalifikovaný název serveru.  
  
 `clsids`  
 Pole CLSID k registraci.  
  
 `factories`  
 Pole rozhraní IUnknown objektů tříd, jejichž dostupnosti je publikován.  
  
 `cookies`  
 Po dokončení operace pole ukazatelé na hodnoty, které identifikují třída objekty, které byly zaregistrovány. Později se používají tyto hodnoty odvolat registrace.  
  
 `count`  
 Počet CLSID k registraci.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK Pokud successfu; jinak hodnota HRESULT například CO_E_OBJISREG, která určuje, z důvodu operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 Objekty COM jsou registrovány CLSCTX_LOCAL_SERVER enumerátor CLSCTX výčtu.  
  
 Typ připojení k registrované objekty je zadána kombinaci aktuální `comflag` parametr šablony a REGCLS_SUSPENDED enumerátor REGCLS výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)