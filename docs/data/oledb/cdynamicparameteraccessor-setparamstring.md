---
title: CDynamicParameterAccessor::SetParamString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
dev_langs:
- C++
helpviewer_keywords:
- SetParamString method
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0b8c435fea707317c1f8de798796f49cb8b048ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095726"
---
# <a name="cdynamicparameteraccessorsetparamstring"></a>CDynamicParameterAccessor::SetParamString
Nastaví data řetězce zadaného parametru uložené ve vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
bool SetParamString(DBORDINAL nParam,   
   constCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,   
   constWCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nParam`  
 [v] Parametr číslo (posun od 1). Parametr 0 je vyhrazena pro vrácené hodnoty. Parametr číslo je index parametru na základě jeho pořadí v SQL nebo uloženou proceduru volání. V tématu [setParam –](../../data/oledb/cdynamicparameteraccessor-setparam.md) příklad.  
  
 `pString`  
 [v] Ukazatel na ANSI (**CHAR**) nebo Unicode (**WCHAR**) řetězcová data zadaný parametr. V tématu `DBSTATUS` v oledb.h.  
  
 *Stav*  
 [v] `DBSTATUS` Stav zadaný parametr. Informace o `DBSTATUS` hodnoty, najdete v části [stav](https://msdn.microsoft.com/en-us/library/ms722617.aspx) v *referenční příručka programátora technologie OLE DB*, nebo vyhledejte `DBSTATUS` v oledb.h.  
  
## <a name="remarks"></a>Poznámky  
 Vrátí **true** v případě úspěchu nebo **false** při selhání.  
  
 `SetParamString` se nezdaří, pokud se pokusíte nastavit řetězec, který je větší než maximální velikost zadaná pro `pString`.  
  
 Použití `SetParamString` nastavit data parametru řetězce ve vyrovnávací paměti. Použití [setParam –](../../data/oledb/cdynamicparameteraccessor-setparam.md) nastavit neřetězcový parametr data ve vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)