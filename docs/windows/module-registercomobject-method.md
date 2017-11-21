---
title: "Module::registercomobject – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs: C++
helpviewer_keywords: RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 69210063663440299639dc2a39a466ecf2df99cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Module – třídy](../windows/module-class.md)