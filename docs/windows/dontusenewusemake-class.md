---
title: Dontusenewusemake – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32418b163cb31f5eaf20c9d2b3ff3a4b585850dd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644096"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake – třída
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class DontUseNewUseMake;  
```  
  
## <a name="remarks"></a>Poznámky  
 Brání použití operátoru **nové** v `RuntimeClass`. V důsledku toho je nutné použít [Make – funkce](../windows/make-function.md) místo.  
  
## <a name="members"></a>Členové  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new – operátor](../windows/dontusenewusemake-operator-new-operator.md)|Přetížení operátoru **nové** a brání použití v `RuntimeClass`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `DontUseNewUseMake`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [Make – funkce](../windows/make-function.md)