---
title: CDynamicAccessor::SetValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
dev_langs:
- C++
helpviewer_keywords:
- SetValue method
ms.assetid: ecc18850-96e5-4845-abe5-ab34ad467238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9322394f2b72b49afe988c371858d9ee580825ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095674"
---
# <a name="cdynamicaccessorsetvalue"></a>CDynamicAccessor::SetValue
Ukládá data na zadaný sloupec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <class ctype>
bool SetValue(   
   DBORDINAL nColumn,   
   constctype& data) throw( );  

template <class ctype>    
bool SetValue(   
   const CHAR * pColumnName,   
   const ctype& data) throw( );  

template <class ctype>   
bool SetValue(  
   const WCHAR *pColumnName,  
   const ctype& data) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 [v] Použitím šablon parametr, který zpracovává všechny typy dat s výjimkou typy řetězec (**CHAR\***, **WCHAR\***), které vyžadují speciální zacházení. `GetValue` používá příslušný datový typ podle co zde určíte.  
  
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