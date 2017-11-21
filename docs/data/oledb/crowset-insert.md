---
title: CRowset::Insert | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.Insert
- CRowset.Insert
- CRowset<TAccessor>.Insert
- CRowset<TAccessor>::Insert
- ATL::CRowset<TAccessor>::Insert
- ATL.CRowset.Insert
- CRowset::Insert
- ATL::CRowset::Insert
dev_langs: C++
helpviewer_keywords: Insert method
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a8cdb6c413cc1a655ace270df632ca501b9b5f3d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetinsert"></a>CRowset::Insert
Vytvoří a inicializuje nový řádek pomocí dat z přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT Insert(   
   int nAccessor = 0,   
   bool bGetHRow = false    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nAccessor`  
 [v] Počet přistupujícího objektu pro vkládání data.  
  
 *bGetHRow*  
 [v] Určuje, jestli se získat popisovač vloženého řádku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje volitelné rozhraní `IRowsetChange`, která nemusí být podporován na všech poskytovatelů; Pokud je to tento případ, vrátí metoda **E_NOINTERFACE**. Musíte taky nastavit **DBPROP_IRowsetChange** k `VARIANT_TRUE` před voláním **otevřete** u tabulky nebo příkazu, který obsahuje sadu řádků.  
  
 Příkaz INSERT může selhat, pokud jeden nebo více sloupců se nedá zapisovat. Upravte mapu kurzor a opravu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro přístup k datovému zdroji prostřednictvím sady řádků a potom vkládání řetězce pomocí tabulky v této sadě řádků.  
  
 Nejdřív vytvořte třídu tabulky vložením nový objekt knihovny ATL do projektu. Například klikněte pravým tlačítkem na projekt v podokně pracovního prostoru a vyberte **nový objekt knihovny ATL**. Z **přístup k datům** kategorie, vyberte **příjemce**. Vytvoření příjemce objektu typu **tabulky**. (Výběr **tabulky** vytvoří sadu řádků přímo z tabulky; výběr **příkaz** vytvoří sadu řádků prostřednictvím příkazu SQL.) Vyberte zdroj dat, zadání tabulky, pomocí kterého je možné získat přístup k danému zdroji dat.. Při volání objektu příjemce **CCustomerTable**, pak by implementovat vložení kódu následujícím způsobem:  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/cpp/crowset-insert_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)