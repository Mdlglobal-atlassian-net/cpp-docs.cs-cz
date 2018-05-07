---
title: CRowset::MoveNext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.MoveNext
- ATL.CRowset.MoveNext
- ATL::CRowset<TAccessor>::MoveNext
- CRowset<TAccessor>.MoveNext
- CRowset.MoveNext
- CRowset<TAccessor>::MoveNext
- CRowset::MoveNext
- ATL::CRowset::MoveNext
dev_langs:
- C++
helpviewer_keywords:
- MoveNext method
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6c56e3dc53699f47c9dc1061120a201ef5698c04
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetmovenext"></a>CRowset::MoveNext
Posune kurzor na další záznam.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT MoveNext() throw();HRESULT MoveNext(LONG lSkip,   
   bool bForward= true) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `lSkip`  
 [v] Počet řádků, které mají přeskočit před načítání.  
  
 `bForward`  
 [v] Předat **true** Přesun na další záznam, **false** přesunout zpátky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`. Pokud bylo dosaženo konce řádků, vrátí **DB_S_ENDOFROWSET**.  
  
## <a name="remarks"></a>Poznámky  
 Načte další po sobě jdoucích řádků ze `CRowset` objekt, nezapomeňte předchozí pozici. Volitelně můžete přeskočit `lSkip` řádků nebo přesunutí zpětné.  
  
 Tato metoda vyžaduje, že nastavíte následující vlastnosti před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků:  
  
-   **DBPROP_CANSCROLLBACKWARDS** musí být `VARIANT_TRUE` Pokud `lSkip` < 0  
  
-   **DBPROP_CANFETCHBACKWARDS** musí být `VARIANT_TRUE` Pokud `bForward` = false  
  
 V opačném případě (Pokud `lSkip` > = 0 a `bForward` = true), není nutné nastavovat žádné další vlastnosti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)   
 [CRowset::MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [CRowset::MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)