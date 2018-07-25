---
title: Module::unregisterobjects – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b711338c436eda3e64d9b51ef0d3137975d834a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874116"
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects – metoda
Zruší registraci objekty v zadaný modul tak, aby ostatní aplikace se nemůže připojit k nim.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UnregisterObjects(  
   ModuleBase* module,  
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>Parametry  
 `module`  
 Ukazatel na modul.  
  
 `serverName`  
 Opravňující název, který určuje podmnožinu objektů vliv na tuto operaci.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je tato operace úspěšná. v opačném chybu HRESULT, která určuje, z důvodu této operace se nezdařila.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)