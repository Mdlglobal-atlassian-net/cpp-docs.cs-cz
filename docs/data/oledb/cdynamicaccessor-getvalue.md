---
title: CDynamicAccessor::GetValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
dev_langs: C++
helpviewer_keywords: GetValue method
ms.assetid: 553f44af-68bc-4cb6-8774-e0940003fa90
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 131c0ebba0ec271a4a92967f677d237703bb592a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetvalue"></a>CDynamicAccessor::GetValue
Načte data pro zadaný sloupec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void* GetValue(   
   DBORDINAL nColumn    
) const throw( );  
void* GetValue(  
   const CHAR* pColumnName   
) const throw( );  
void* GetValue(  
   const WCHAR* pColumnName   
) const throw( );  
template < class ctype >  
bool GetValue(  
   DBORDINAL nColumn,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const CHAR* pColumnName,  
   ctype* pData   
) const throw( );  
template < class ctype >  
bool GetValue(  
   const WCHAR* pColumnName,  
   ctype* pData   
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 [v] Použitím šablon parametr, který zpracovává všechny typy dat s výjimkou typy řetězec (**CHAR\***, **WCHAR\***), které vyžadují speciální zacházení. `GetValue`používá příslušný datový typ podle co zde určíte.  
  
 `nColumn`  
 [v] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.  
  
 `pColumnName`  
 [v] Název sloupce.  
  
 `pData`  
 [out] Ukazatel na obsah pro určený sloupec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud chcete k předávání dat řetězec, použijte nontemplated verze `GetValue`. Verze nontemplated této metody vrátit **void\***, která odkazuje na část vyrovnávací paměť, která obsahuje data zadaný sloupec. Vrátí **NULL** Pokud sloupec nebyl nalezen.  
  
 Pro všechny ostatní typy dat, je jednodušší použít podle šablony verze `GetValue`. Vrátí podle šablony verze **true** v případě úspěchu nebo **false** při selhání.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí verze nontemplated vrátit sloupce, které obsahují řetězce a podle šablony verze pro sloupce, které obsahují jiné datové typy.  
  
 V režimu ladění, zobrazí se kontrolní výrazy Pokud velikost `pData` nerovné velikosti sloupce, na kterou odkazuje.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)