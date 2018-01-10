---
title: CRowset::Undo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset.Undo
- ATL::CRowset<TAccessor>::Undo
- CRowset<TAccessor>::Undo
- ATL.CRowset.Undo
- ATL.CRowset<TAccessor>.Undo
- CRowset<TAccessor>.Undo
- ATL::CRowset::Undo
- CRowset::Undo
- Undo
dev_langs: C++
helpviewer_keywords: Undo method
ms.assetid: 1ccd70e2-3931-41c4-893e-a05d0e295410
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d56be5cbaf5f8c3393527c59319cdda4aca124e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetundo"></a>CRowset::Undo
Vrátí zpět všechny změny na řádek od posledního načtení nebo [aktualizace](../../data/oledb/crowset-update.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT Undo(   
   DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcRows`  
 [out] Ukazatel do umístění, kde **vrátit zpět** vrátí počet řádků, které se pokusil vrátit zpět v případě potřeby.  
  
 `phRow`  
 [out] Ukazatel do umístění, kde **vrátit zpět** vrátí pole popisovačů pro všechny řádky se pokusil vrátit zpět v případě potřeby.  
  
 `pStatus`  
 [out] Ukazatel do umístění, kde **vrátit zpět** vrátí hodnotu stavový řádek. Pokud je vrácen žádný stav `pStatus` má hodnotu null.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetUpdate`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetUpdate** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)