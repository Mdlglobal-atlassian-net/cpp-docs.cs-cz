---
title: CCommand::GetNextResult | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
dev_langs:
- C++
helpviewer_keywords:
- GetNextResult method
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 424390a116cfad18dc3221efbc26a05ea666f122
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ccommandgetnextresult"></a>CCommand::GetNextResult
Načte další výsledek nastavit, pokud je k dispozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,  
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pulRowsAffected*  
 [vstup/výstup] Ukazatel na paměti, kde je vrácen počet ovlivněných příkazem řádků.  
  
 `bBind`  
 [v] Určuje, jestli se vytvořit vazbu příkaz automaticky po spouštěna. Výchozí hodnota je **true**, což způsobí, že příkaz, který má být vázána automaticky. Nastavení `bBind` k **false** brání automatické vazby příkaz tak, aby můžete ručně vytvořit vazbu. (Ruční vazba je zajímají hlavně o uživatelům OLAP).  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je sada výsledků dotazu byla dříve získána, tato funkce uvolní předchozí sadu výsledků dotazu a odpojuje sloupce. Pokud `bBind` je **true**, se váže nové sloupce.  
  
 Tato funkce by měly volat, pouze v případě, že jste zadali více výsledků nastavením `CCommand` parametr šablony *TMultiple*=`CMultipleResults`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CCommand – třída](../../data/oledb/ccommand-class.md)