---
title: CRowset::MoveNext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.MoveNext
- ATL.CRowset.MoveNext
- ATL::CRowset<TAccessor>::MoveNext
- CRowset<TAccessor>.MoveNext
- CRowset.MoveNext
- CRowset<TAccessor>::MoveNext
- CRowset::MoveNext
- ATL::CRowset::MoveNext
dev_langs: C++
helpviewer_keywords: MoveNext method
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bd997b25125a48dd6103629e6957843295532901
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovenext"></a>CRowset::MoveNext
Posune kurzor na další záznam.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT MoveNext( ) throw( );   
HRESULT MoveNext(   
   LONG lSkip,   
   bool bForward = true    
) throw( );  
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