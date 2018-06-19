---
title: CCommand::GetNextResult | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d833c3e644ac6ed44216542ce4fc6d995cc22efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094192"
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