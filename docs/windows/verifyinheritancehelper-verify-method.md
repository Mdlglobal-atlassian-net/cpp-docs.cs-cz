---
title: Verifyinheritancehelper::Verify – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: 04bf01b5fad5a9fec579e347497a28b5e8abb861
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018813"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
static void Verify();  
```  
  
## <a name="remarks"></a>Poznámky  
 Testuje dvě rozhraní určeném aktuálním parametry šablony a určuje, zda jedno rozhraní je odvozena od druhé.  
  
 Chyba je vygenerován, pokud jedno rozhraní není odvozena od druhé.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Verifyinheritancehelper – struktura](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)