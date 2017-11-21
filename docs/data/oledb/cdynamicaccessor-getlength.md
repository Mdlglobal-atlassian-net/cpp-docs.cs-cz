---
title: CDynamicAccessor::GetLength | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
dev_langs: C++
helpviewer_keywords: GetLength method
ms.assetid: 3ae8983b-b267-4cf9-bfc0-3e191f79e646
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6d62a4d23bb25fec0f85b5230b0136b745fb0801
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetlength"></a>CDynamicAccessor::GetLength
Načte délka zadaný sloupec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      bool GetLength(   
   DBORDINAL nColumn,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const CHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
bool GetLength(   
   const WCHAR* pColumnName,   
   DBLENGTH* pLength    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [v] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.  
  
 `pColumnName`  
 [v] Ukazatel na řetězec znaků, který obsahuje název sloupce.  
  
 `pLength`  
 [out] Ukazatel na celé číslo obsahující délku sloupce v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud je nalezen zadaný sloupec. Jinak, funkce vrátí hodnotu **false**.  
  
## <a name="remarks"></a>Poznámky  
 První přepsání trvá číslo sloupce a druhý a třetí přepsání trvat název sloupce ve formátu ANSI nebo Unicode, v uvedeném pořadí.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicAccessor::SetLength](../../data/oledb/cdynamicaccessor-setlength.md)