---
title: CRowset::GetApproximatePosition | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::GetApproximatePosition
- ATL::CRowset<TAccessor>::GetApproximatePosition
- CRowset.GetApproximatePosition
- CRowset::GetApproximatePosition
- GetApproximatePosition
- ATL.CRowset.GetApproximatePosition
- CRowset<TAccessor>::GetApproximatePosition
dev_langs: C++
helpviewer_keywords: GetApproximatePosition method
ms.assetid: 8f9ccd41-0590-468e-b202-6731d0f99d21
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 165537f3b61120237e7bfb8330ecf353bc01a107
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetgetapproximateposition"></a>CRowset::GetApproximatePosition
Vrátí přibližnou pozice řádku odpovídající záložky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT GetApproximatePosition(   
   const CBookmarkBase* pBookmark,   
   DBCOUNTITEM* pPosition,   
   DBCOUNTITEM* pcRows    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBookmark`  
 [v] Ukazatel na záložku, která identifikuje řádek, jejíž pozice s má být nalezen. **NULL** Pokud pouze počet řádků je povinný.  
  
 *pPosition*  
 [out] Ukazatel do umístění, kde `GetApproximatePosition` vrátí pozice řádků. **NULL** Pokud pozici není potřeba.  
  
 `pcRows`  
 [out] Ukazatel do umístění, kde `GetApproximatePosition` vrátí celkový počet řádků. **NULL** Pokud počet řádků není potřeba.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetScroll`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetScroll** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
 Informace o použití záložek uživatele najdete v tématu [pomocí záložky](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [IRowsetScroll::GetApproximatePosition](https://msdn.microsoft.com/en-us/library/ms712901.aspx)