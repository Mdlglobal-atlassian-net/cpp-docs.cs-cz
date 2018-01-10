---
title: "Nastavení vlastností ve zprostředkovateli | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1da48eb2439b94f326380b9991ea63d548131628
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="setting-properties-in-your-provider"></a>Nastavení vlastností ve zprostředkovateli
Pro vlastnost, kterou chcete najít skupinu vlastností a vlastnost ID. Další informace najdete v tématu [vlastnosti technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
 V kódu zprostředkovatele je vygenerovat průvodcem najdete mapa vlastností odpovídající skupině vlastností. Název skupiny vlastností obvykle odpovídá názvu objektu. Vlastnosti příkazu a sady řádků lze nalézt v příkazu nebo sady řádků; Vlastnosti zdroje a inicializace dat naleznete v objektu zdroje dat.  
  
 Vlastnosti mapy, přidejte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) makro. PROPERTY_INFO_ENTRY_EX mají čtyři parametry:  
  
-   ID vlastnosti odpovídající vaší vlastnosti. Nejprve sedm znaky ("DBPROP_") je nutné odebrat z před název vlastnosti. Pokud chcete přidat například **DBPROP_MAXROWS**, předat `MAXROWS` jako první prvek. Pokud se jedná vlastní vlastnost, předejte úplný název identifikátor GUID (například `DBMYPROP_MYPROPERTY`).  
  
-   Typ varianty vlastnosti (v [vlastnosti technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms722734.aspx) v *referenční příručka programátora technologie OLE DB*). Zadejte **typ VT_** typu (například `VT_BOOL` nebo `VT_I2`) odpovídající na datový typ.  
  
-   Příznaky znamená, zda je vlastnost pro čtení a zápis a skupiny, do které patří. Následující kód například označuje vlastnost pro čtení a zápis patří do skupiny řádků:  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   Hodnotu vlastnosti. To může být **VARIANT_FALSE** logická hodnota. Zadejte nebo má nulovou hodnotu pro typ integer, např. Vlastnost má tuto hodnotu, pokud se změní.  
  
    > [!NOTE]
    >  Některé vlastnosti jsou připojené nebo zřetězené na další vlastnosti, jako je například záložky nebo aktualizaci. Pokud příjemce nastaví jednu vlastnost na hodnotu true, může být také nastavena jinou vlastnost. Šablony zprostředkovatele technologie OLE DB podporují prostřednictvím metody [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).  
  
## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Vlastnosti ignorovat zprostředkovatele Microsoft OLE DB  
 Zprostředkovatele Microsoft OLE DB ignorovat následující vlastnosti OLE DB:  
  
-   **DBPROP_MAXROWS** funguje výhradně u zprostředkovatelé jen pro čtení (to znamená, kde DBPROP_IRowsetChange a DBPROP_IRowsetUpdate jsou false); jinak tato vlastnost není podporována.  
  
-   **DBPROP_MAXPENDINGROWS** je ignorován; zprostředkovatele určuje vlastní limit.  
  
-   **DBPROP_MAXOPENROWS** je ignorován; zprostředkovatele určuje vlastní limit.  
  
-   **DBPROP_CANHOLDROWS** je ignorován; zprostředkovatele určuje vlastní limit.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)