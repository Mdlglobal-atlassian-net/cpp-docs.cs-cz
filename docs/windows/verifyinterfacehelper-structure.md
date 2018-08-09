---
title: Verifyinterfacehelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
dev_langs:
- C++
helpviewer_keywords:
- VerifyInterfaceHelper structure
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b1dd40487a9d843fb81be1e0be65d76a86e1f9c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013295"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper – struktura
Podporuje knihovny šablon jazyka C++ Windows Runtime infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   bool isWinRTInterface,  
   typename I  
>  
struct VerifyInterfaceHelper;  
  
template <  
   typename I  
>  
struct VerifyInterfaceHelper<false, I>;  
```  
  
### <a name="parameters"></a>Parametry  
 *I*  
 Rozhraní pro ověření.  
  
 *isWinRTInterface*  
  
## <a name="remarks"></a>Poznámky  
 Ověřuje, že rozhraní určené parametrem šablony splňuje určité požadavky.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[VerifyInterfaceHelper::Verify – metoda](../windows/verifyinterfacehelper-verify-method.md)||  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `VerifyInterfaceHelper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)