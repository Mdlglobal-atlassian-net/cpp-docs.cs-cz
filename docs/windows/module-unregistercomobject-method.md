---
title: "Module::unregistercomobject – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs: C++
helpviewer_keywords: UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43ea6ab8f3990316be7bce27c06b3aee0df8fbf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject – metoda
Odregistruje jeden nebo více objektů COM, což zabraňuje dalších aplikací v připojení k nim.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
virtual HRESULT UnregisterCOMObject(  
   const wchar_t* serverName,  
   DWORD* cookies,  
   unsigned int count  
```  
  
#### <a name="parameters"></a>Parametry  
 `serverName`  
 (Nepoužívané)  
  
 `cookies`  
 Pole ukazatelé na hodnoty, které identifikují objekty tříd být neregistrované. Pole byl vytvořen [registercomobject –](../windows/module-registercomobject-method.md) metoda.  
  
 `count`  
 Počet tříd se zrušit registraci.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je tato operace úspěšná. v opačném chybu HRESULT, která určuje, z důvodu operace se nezdařila.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třídy](../windows/module-class.md)