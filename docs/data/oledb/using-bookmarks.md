---
title: "Použití záložek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 41c8e5a44130eebfddc9e99ab7ef815b6e8e43a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-bookmarks"></a>Použití záložek
Před otevřením sady řádků se musí zjistit poskytovatele, kterou chcete použít záložky. Chcete-li to provést, nastavte **DBPROP_BOOKMARKS** vlastnost, která má **true** ve vašem vlastnost nastavit. Zprostředkovatel načte záložky jako sloupec nule, je nutné použít speciální makro `BOOKMARK_ENTRY` a `CBookmark` třídy, pokud používáte statické přistupujícího objektu. `CBookmark`je třída šablony, kde je argument délka v bajtech vyrovnávací paměti záložky. Délka vyrovnávací paměti vyžadované pro záložky závisí na poskytovateli. Pokud používáte zprostředkovatele ODBC OLE DB, jak je znázorněno v následujícím příkladu, musí být vyrovnávací paměti 4 bajtů.  
  
```  
class CProducts  
{  
public:  
   CBookmark<4>   bookmark;  
  
   BEGIN_COLUMN_MAP(CProducts)  
      BOOKMARK_ENTRY(bookmark)  
   END_COLUMN_MAP()  
};  
  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_BOOKMARKS, true);  
  
CTable<CAccessor<CProducts> > product;  
product.Open(session, "Products", &propset);  
```  
  
 Pokud používáte `CDynamicAccessor`, vyrovnávací paměť se přidělí dynamicky za běhu. V takovém případě můžete použít specializovanou verzi `CBookmark` pro kterou nezadávejte velikost vyrovnávací paměti. Pomocí funkce `GetBookmark` k načtení záložky z na aktuální záznam, jak je znázorněno v této ukázce kódu:  
  
```  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  
propset.AddProperty(DBPROP_BOOKMARKS, true);  
product.Open(session, "Products", &propset);  
product.MoveNext();  
product.GetBookmark(&bookmark);  
```  
  
 Informace o podpoře záložek ve zprostředkovatelích najdete v tématu [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)