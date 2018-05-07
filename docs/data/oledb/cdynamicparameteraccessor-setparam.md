---
title: CDynamicParameterAccessor::SetParam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
dev_langs:
- C++
helpviewer_keywords:
- SetParam method
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 37f60999eb87d473fb51bb0a493a79d0edf96074
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorsetparam"></a>CDynamicParameterAccessor::SetParam
Nastaví parametr vyrovnávací paměti, pomocí zadaná data (jiné než řetězec).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,  
               constctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  

template <class ctype>  
bool SetParam(TCHAR* pParamName,  
               const ctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 Použitím šablon parametr, který je datového typu.  
  
 `nParam`  
 [v] Parametr číslo (posun od 1). Parametr 0 je vyhrazena pro vrácené hodnoty. Parametr číslo je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. Příklad:  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 [v] Název parametru.  
  
 `pData`  
 [v] Ukazatel na paměť obsahující data, která mají být zapsána do vyrovnávací paměti.  
  
 *Stav*  
 [v] `DBSTATUS` Sloupec Stav. Informace o `DBSTATUS` hodnoty, najdete v části [stav](https://msdn.microsoft.com/en-us/library/ms722617.aspx) v *referenční příručka programátora technologie OLE DB*, nebo vyhledejte `DBSTATUS` v oledb.h.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** v případě úspěchu nebo **false** při selhání.  
  
 Použití `SetParam` nastavit neřetězcový parametr data ve vyrovnávací paměti. Použití [setparamstring –](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) nastavit data parametru řetězce ve vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)