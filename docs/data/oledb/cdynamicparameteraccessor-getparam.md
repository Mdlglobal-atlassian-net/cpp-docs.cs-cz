---
title: CDynamicParameterAccessor::GetParam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
dev_langs:
- C++
helpviewer_keywords:
- GetParam method
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3596cf8fc445a5607c008be687c44cafb713049b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorgetparam"></a>CDynamicParameterAccessor::GetParam
Načte data neřetězcový pro zadaný parametr z vyrovnávací paměti parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,   
  ctype* pData) const throw();  

template <class ctype> bool GetParam(TCHAR* pParamName,   
   ctype* pData) const throw();  

void* GetParam(DBORDINAL nParam) const throw();  

void* GetParam(TCHAR* pParamName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 Použitím šablon parametr, který je datového typu.  
  
 `nParam`  
 [v] Parametr číslo (posun od 1). Parametr 0 je vyhrazena pro vrácené hodnoty. Parametr číslo je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. V tématu [setParam –](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.  
  
 `pParamName`  
 [v] Název parametru.  
  
 `pData`  
 [out] Ukazatel na paměti, který obsahuje data načtená z vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 U verzí nontemplated odkazuje na paměti, který obsahuje data načíst z vyrovnávací paměti. U šablonované verzí, vrátí **true** v případě úspěchu nebo **false** při selhání.  
  
 Použití `GetParam` k načtení neřetězcový parametr dat z vyrovnávací paměti. Použití [getparamstring –](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) načíst data parametru řetězce z vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)