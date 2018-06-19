---
title: Terminatemap – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4787fec0a6b4b9f55c500b66786372945d9a523
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890346"
---
# <a name="terminatemap-function"></a>TerminateMap – funkce
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
## <a name="parameters"></a>Parametry  
 `module`  
 A [modulu](../windows/module-class.md).  
  
 `serverName`  
 Název podmnožinu objekty pro vytváření tříd v modulu určený parametrem `module`.  
  
 `forceTerminate`  
 `true` Ukončit třídu objektů Factory bez ohledu na to, že jsou aktivní; `false` není ukončen objekty pro vytváření tříd, pokud je aktivní žádné objekt pro vytváření.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud byla ukončena všechny objekty pro vytváření tříd; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Vypne tříd v zadaný modul.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)