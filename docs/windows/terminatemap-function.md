---
title: "Terminatemap – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::TerminateMap
dev_langs: C++
helpviewer_keywords: TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: efe6b143c2fe9a48a008f9005244178b436d170e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 `true`Ukončit třídu objektů Factory bez ohledu na to, že jsou aktivní; `false` není ukončen objekty pro vytváření tříd, pokud je aktivní žádné objekt pro vytváření.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud byla ukončena všechny objekty pro vytváření tříd; v opačném `false`.  
  
## <a name="remarks"></a>Poznámky  
 Vypne tříd v zadaný modul.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)