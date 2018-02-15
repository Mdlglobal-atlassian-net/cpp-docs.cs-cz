---
title: CDynamicParameterAccessor::GetParamLength | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
dev_langs:
- C++
helpviewer_keywords:
- GetParamLength method
ms.assetid: 04d76931-911a-4915-9c2c-ad585a9f3854
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c60f2a294019b269535a9f2f1debf5d257d9c242
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicparameteraccessorgetparamlength"></a>CDynamicParameterAccessor::GetParamLength
Načte délka zadaný parametr uložené ve vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
bool GetParamLength(DBORDINAL nParam,  
  DBLENGTH* pLength);  

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nParam`  
 [v] Parametr číslo (posun od 1). Parametr 0 je vyhrazena pro vrácené hodnoty. Parametr číslo je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. V tématu [setParam –](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.  
  
 `pLength`  
 [out] Ukazatel na proměnnou obsahující délku v bajtech zadaný parametr.  
  
## <a name="remarks"></a>Poznámky  
 První přepsat vrátí **true** v případě úspěchu nebo **false** při selhání. Druhý přepsat odkazuje na paměti, který obsahuje délku parametru.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)