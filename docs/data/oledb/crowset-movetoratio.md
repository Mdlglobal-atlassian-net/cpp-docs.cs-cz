---
title: CRowset::MoveToRatio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MoveToRatio
- CRowset<TAccessor>::MoveToRatio
- CRowset::MoveToRatio
- CRowset<TAccessor>.MoveToRatio
- ATL.CRowset.MoveToRatio
- ATL::CRowset::MoveToRatio
- CRowset.MoveToRatio
- ATL.CRowset<TAccessor>.MoveToRatio
- ATL::CRowset<TAccessor>::MoveToRatio
dev_langs:
- C++
helpviewer_keywords:
- MoveToRatio method
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df1e7f51fb1bf82ced62c18a863f25870a4e4493
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetmovetoratio"></a>CRowset::MoveToRatio
Načte řádky od zlomkové pozice v dané sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,bool bForward = true) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nNumerator`  
 [v] Používá k určení zlomkové čítači poziční, ze kterého chcete načíst data.  
  
 `nDenominator`  
 [v] Jmenovatel používá k určení zlomkové poziční, ze kterého chcete načíst data.  
  
 `bForward`  
 [v] Označuje, zda přesunutí nebo předchozí. Výchozí hodnota je předat dál.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 `MoveToRatio` načte řádky zhruba podle následující vzorec:  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 Kde `RowsetSize` je velikost řádků, měřená v řádků. Přesnost tento vzorec závisí na konkrétního zprostředkovatele. Podrobnosti najdete v tématu [IRowsetScroll::GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx).  
  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetScroll`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetScroll** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)