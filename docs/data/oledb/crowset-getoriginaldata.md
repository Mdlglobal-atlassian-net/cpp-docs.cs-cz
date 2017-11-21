---
title: CRowset::GetOriginalData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.GetOriginalData
- CRowset<TAccessor>::GetOriginalData
- GetOriginalData
- ATL::CRowset<TAccessor>::GetOriginalData
- ATL.CRowset.GetOriginalData
- CRowset::GetOriginalData
- ATL::CRowset::GetOriginalData
- CRowset.GetOriginalData
dev_langs: C++
helpviewer_keywords: GetOriginalData method
ms.assetid: 5b69d30e-34f4-41a4-a82d-cd175be88d53
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7a1c5fe26d17ac353138abc21b3ae46d9a72101
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetgetoriginaldata"></a>CRowset::GetOriginalData
Volání **IRowsetUpdate::GetOriginalData** k načtení požadovaných dat naposledy načtených z nebo přeneseno do zdroje dat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT GetOriginalData( ) throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načítá data z naposledy načteno nebo přeneseno do zdroje dat; nenačítá hodnot na základě změny čekající na zpracování.  
  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetUpdate`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetUpdate** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)