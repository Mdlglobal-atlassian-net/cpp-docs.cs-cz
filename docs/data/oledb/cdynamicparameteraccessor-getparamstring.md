---
title: CDynamicParameterAccessor::GetParamString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
dev_langs:
- C++
helpviewer_keywords:
- GetParamString method
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5ee0bb1dce2206902f6ccf1ed331d5c843690ce0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicparameteraccessorgetparamstring"></a>CDynamicParameterAccessor::GetParamString
Načte řetězec data zadaný parametr uložené ve vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
bool GetParamString(DBORDINAL nParam,  
  CSimpleStringA& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CSimpleStringW& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CHAR* pBuffer,  
   size_t* pMaxLen) throw();bool GetParamString(DBORDINAL nParam,  
  WCHAR* pBuffer,  
   size_t* pMaxLen) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nParam`  
 [v] Parametr číslo (posun od 1). Parametr 0 je vyhrazena pro vrácené hodnoty. Parametr číslo je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. V tématu [setParam –](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.  
  
 `strOutput`  
 [out] ANSI (**CSimpleStringA**) nebo Unicode (**CSimpleStringW**) řetězcová data zadaný parametr. Parametr typu by měla předávat `CString`, například:  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 [out] Ukazatel na ANSI (**CHAR**) nebo Unicode (**WCHAR**) řetězcová data zadaný parametr.  
  
 `pMaxLen`  
 [out] Ukazatel na velikost vyrovnávací paměti na kterou odkazuje `pBuffer` (ve znacích, včetně ukončující NULL).  
  
## <a name="remarks"></a>Poznámky  
 Vrátí **true** v případě úspěchu nebo **false** při selhání.  
  
 Pokud `pBuffer` má hodnotu NULL, tato metoda nastaví velikost vyrovnávací paměti požadovaná v paměti, na kterou odkazuje `pMaxLen` a vrátit **true** bez kopírování dat.  
  
 Tato metoda se nezdaří, pokud vyrovnávací paměť `pBuffer` není dostatečně velký, aby se tak, aby obsahovala celý řetězec.  
  
 Použití `GetParamString` načíst data parametru řetězce z vyrovnávací paměti. Použití [GetParam –](../../data/oledb/cdynamicparameteraccessor-getparam.md) k načtení neřetězcový parametr dat z vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)