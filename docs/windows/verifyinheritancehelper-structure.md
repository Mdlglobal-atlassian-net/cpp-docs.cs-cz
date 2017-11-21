---
title: "Verifyinheritancehelper – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::VerifyInheritanceHelper
dev_langs: C++
helpviewer_keywords: VerifyInheritanceHelper structure
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 926ed226b67ae510647d2523e4992f6ee3c79a5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename I,  
   typename Base  
>  
struct VerifyInheritanceHelper;  
template <  
   typename I  
>  
struct VerifyInheritanceHelper<I, Nil>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I`  
 Typ.  
  
 `Base`  
 Jiný typ.  
  
## <a name="remarks"></a>Poznámky  
 Ověřuje, zda jedno rozhraní je odvozený od jiného rozhraní.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Verifyinheritancehelper::Verify – metoda](../windows/verifyinheritancehelper-verify-method.md)|Testuje dvě rozhraní zadanou aktuální parametry šablony a určuje, zda jedno rozhraní je odvozena z jiných.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `VerifyInheritanceHelper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)