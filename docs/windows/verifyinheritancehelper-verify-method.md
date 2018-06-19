---
title: Verifyinheritancehelper::Verify – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 879f5fa117f0f2bc444243f540925d64a2b824b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889872"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static void Verify();  
```  
  
## <a name="remarks"></a>Poznámky  
 Testuje dvě rozhraní zadanou aktuální parametry šablony a určuje, zda jedno rozhraní je odvozena z jiných.  
  
 Pokud jedno rozhraní není odvozen z jiných, jsou vydávány k chybě.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Verifyinheritancehelper – struktura](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)