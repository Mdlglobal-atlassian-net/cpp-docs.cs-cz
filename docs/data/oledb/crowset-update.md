---
title: CRowset::Update | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset.Update
- ATL.CRowset.Update
- ATL.CRowset<TAccessor>.Update
- ATL::CRowset<TAccessor>::Update
- CRowset<TAccessor>::Update
- CRowset::Update
- CRowset<TAccessor>.Update
- ATL::CRowset::Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac465bdb5cfa228e5621a3ccf0d791f5f5271421
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetupdate"></a>CRowset::Update
Odesílá všechny neuložené změny provedené na aktuální řádek od posledního načtení nebo **aktualizace** volání na něm.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Update(DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcRows`  
 [out] Ukazatel do umístění, kde **aktualizace** vrátí počet řádků, které se pokusil aktualizovat, pokud je to nutné.  
  
 `phRow`  
 [out] Ukazatel do umístění, kde **aktualizace** vrátí popisovač řádku se pokusil aktualizovat. Žádná obslužná rutina je vrácena v případě `phRow` má hodnotu null.  
  
 `pStatus`  
 [out] Ukazatel do umístění, kde **aktualizace** vrátí hodnotu stavový řádek. Pokud je vrácen žádný stav `pStatus` má hodnotu null.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Odesílá všechny neuložené změny provedené na aktuální řádek od posledního načtených nebo aktualizovat tento řádek (pomocí **aktualizace** nebo [UpdateAll –](../../data/oledb/crowset-updateall.md)). Obvykle volání [SetData](../../data/oledb/crowset-setdata.md) nastavit datových hodnot ve sloupcích v řádku, a pak zavolají **aktualizace** přenést tyto změny.  
  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetUpdate`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetUpdate** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)