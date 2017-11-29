---
title: CDynamicAccessor::SetValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs: C++
helpviewer_keywords: SetValue method
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 194b87d9422f3e2ebf80fa647353c0cc6f72a5b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorsetvalue"></a>CDynamicAccessor::SetValue
Ukládá data na zadaný sloupec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      template < class ctype >    
bool SetValue(   
   DBORDINAL nColumn,   
   const ctype& data    
) throw( );  
template < class ctype >    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data    
) throw( );  
template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 [v] Použitím šablon parametr, který zpracovává všechny typy dat s výjimkou typy řetězec (**CHAR\***, **WCHAR\***), které vyžadují speciální zacházení. `GetValue`používá příslušný datový typ podle co zde určíte.  
  
 `pColumnName`  
 [v] Ukazatel na řetězec znaků, který obsahuje název sloupce.  
  
 `data`  
 [v] Ukazatel na paměti, který obsahuje data.  
  
 `nColumn`  
 [v] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud chcete nastavit řetězec dat, použijte nontemplated verze `GetValue`. Verze nontemplated této metody vrátit **void\***, která odkazuje na část vyrovnávací paměť, která obsahuje data zadaný sloupec. Vrátí **NULL** Pokud sloupec nebyl nalezen.  
  
 Pro všechny ostatní typy dat, je jednodušší použít podle šablony verze `GetValue`. Vrátí podle šablony verze **true** v případě úspěchu nebo **false** při selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)