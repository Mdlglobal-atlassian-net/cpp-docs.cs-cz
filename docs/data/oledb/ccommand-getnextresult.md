---
title: CCommand::GetNextResult | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
dev_langs: C++
helpviewer_keywords: GetNextResult method
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a0b4c03d7aa31949752e4362380d1705d7db6e9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandgetnextresult"></a>CCommand::GetNextResult
Načte další výsledek nastavit, pokud je k dispozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT GetNextResult(  
   DBROWCOUNT* pulRowsAffected,  
   bool bBind = true   
) throw( );  
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