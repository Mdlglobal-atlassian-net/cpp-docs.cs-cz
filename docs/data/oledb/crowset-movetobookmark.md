---
title: CRowset::MoveToBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::MoveToBookmark
- ATL::CRowset<TAccessor>::MoveToBookmark
- ATL.CRowset.MoveToBookmark
- ATL.CRowset<TAccessor>.MoveToBookmark
- MoveToBookmark
- CRowset::MoveToBookmark
- CRowset.MoveToBookmark
- CRowset<TAccessor>::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2e443cace051fc0d5c08381222f0cd6aa53bec8f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetmovetobookmark"></a>CRowset::MoveToBookmark
Načte řádek označený záložku nebo řádek na zadaný posun (`lSkip`) z tuto záložku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,   
   LONG lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `bookmark`  
 [v] Záložku označení umístění, ze kterého chcete načíst data.  
  
 `lSkip`  
 [v] Číslo počet řádků z záložky na cílový řádek. Pokud `lSkip` rovná nule, načtených první řádek je řádek označený záložkou. Pokud `lSkip` je 1, načtených první řádek je řádek po řádku záložkou. Pokud `lSkip` je -1, načtených první řádek je řádek před záložkou řádek.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetLocate`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetLocate** k `VARIANT_TRUE` a nastavte **DBPROP_CANFETCHBACKWARDS** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkaz obsahující dané sadě řádků.  
  
 Informace o použití záložek uživatele najdete v tématu [pomocí záložky](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate::GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)