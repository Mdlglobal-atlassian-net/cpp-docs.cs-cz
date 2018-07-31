---
title: Nastavení vlastností ve zprostředkovateli | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7fedb77b6ede8d9fa843e7e7cdd344e03efecede
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337895"
---
# <a name="setting-properties-in-your-provider"></a>Nastavení vlastností ve zprostředkovateli
Najdete skupinu vlastností a vlastnost ID pro požadovanou vlastnost. Další informace najdete v tématu [vlastnosti technologie OLE DB](https://msdn.microsoft.com/library/ms722734.aspx) v *OLE DB referenční informace pro programátory*.  
  
 V kódu zprostředkovatele generované průvodcem knihovnou vyhledejte mapování vlastnosti odpovídající vlastnosti skupiny. Název skupiny vlastností obvykle odpovídá názvu objektu. Vlastnosti příkazu a sady řádků lze nalézt v příkazu nebo sady řádků; Vlastnosti datového zdroje a inicializace naleznete v objektu zdroje dat.  
  
 Vlastnosti mapy, přidejte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) – makro. PROPERTY_INFO_ENTRY_EX přebírá čtyři parametry:  
  
-   ID vlastnosti odpovídající vaší vlastnosti. Prvních 7 znaků ("DBPROP_") je třeba odebrat z přední části názvu vlastnosti. Pokud chcete přidat například `DBPROP_MAXROWS`, předejte `MAXROWS` jako prvního prvku. Pokud se jedná vlastní vlastnost, předejte úplný název identifikátoru GUID (například `DBMYPROP_MYPROPERTY`).  
  
-   Typ varianty vlastnosti (v [vlastnosti technologie OLE DB](https://msdn.microsoft.com/library/ms722734.aspx) v *OLE DB referenční informace pro programátory*). Zadejte odpovídající typ VT_ typ (například VT_BOOL nebo VT_I2) do datového typu.  
  
-   Příznaky, které označují, zda je vlastnost pro čtení a pro zápis a skupiny, do které patří. Například následující kód označuje vlastnost pro čtení a zápis patří do skupiny řádků:  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   Základní hodnoty vlastnosti. To může být `VARIANT_FALSE` logickou hodnotu typu nebo má nulovou hodnotu pro typ integer, třeba. Vlastnost má tuto hodnotu, pokud se změní.  
  
    > [!NOTE]
    >  Některé vlastnosti jsou připojené nebo připojený k jiné vlastnosti, jako je například záložek nebo aktualizaci. Pokud příjemce jednu vlastnost nastaví na hodnotu true, může být také nastavena jiné vlastnosti. Šablony zprostředkovatele OLE DB podporují prostřednictvím metody [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).  
  
## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Vlastnosti nastavení ignoruje zprostředkovatele Microsoft OLE DB  
 Zprostředkovatele Microsoft OLE DB ignorovat následující vlastnosti OLE DB:  
  
-   `DBPROP_MAXROWS` funguje pouze pro zprostředkovatele pouze pro čtení (to znamená, kde DBPROP_IRowsetChange a DBPROP_IRowsetUpdate jsou false); jinak tato vlastnost není podporována.  
  
-   `DBPROP_MAXPENDINGROWS` se ignoruje; zprostředkovatel určuje vlastní omezení.  
  
-   `DBPROP_MAXOPENROWS` se ignoruje; zprostředkovatel určuje vlastní omezení.  
  
-   `DBPROP_CANHOLDROWS` se ignoruje; zprostředkovatel určuje vlastní omezení.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)