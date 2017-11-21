---
title: CDynamicParameterAccessor::SetParamString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
dev_langs: C++
helpviewer_keywords: SetParamString method
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ff96f451bc60469df0469d6a002ec51d91743b89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicparameteraccessorsetparamstring"></a>CDynamicParameterAccessor::SetParamString
Nastaví data řetězce zadaného parametru uložené ve vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      bool SetParamString(   
   DBORDINAL nParam,   
   const CHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
bool SetParamString(   
   DBORDINAL nParam,   
   const WCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
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
  
 `SetParamString`se nezdaří, pokud se pokusíte nastavit řetězec, který je větší než maximální velikost zadaná pro `pString`.  
  
 Použití `SetParamString` nastavit data parametru řetězce ve vyrovnávací paměti. Použití [setParam –](../../data/oledb/cdynamicparameteraccessor-setparam.md) nastavit neřetězcový parametr data ve vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)