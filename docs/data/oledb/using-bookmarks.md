---
title: Použití záložek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d8d23ba81ba83202da1dd6814374a0c4aa1cb98b
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990065"
---
# <a name="using-bookmarks"></a>Použití záložek

Před otevřením v sadě řádků musí sdělte poskytovateli, že chcete používat záložky. Chcete-li to provést, nastavte `DBPROP_BOOKMARKS` vlastnost **true** ve vaší vlastnost nastavit. Zprostředkovatel načte záložky jako sloupec nula, je nutné použít speciální makro BOOKMARK_ENTRY a `CBookmark` třídy, pokud používáte statického následovníka. `CBookmark` je třída šablony, kde je argument délku vyrovnávací paměti záložek v bajtech. Délka vyrovnávací paměti vyžadované pro záložku závisí na poskytovateli. Pokud používáte zprostředkovatele ODBC OLE DB, jak je znázorněno v následujícím příkladu, musí být vyrovnávací paměti 4 bajty.  
  
```cpp  
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
  
CTable<CAccessor<CProducts>> product;  
product.Open(session, "Products", &propset);  
```  
  
Pokud používáte `CDynamicAccessor`, vyrovnávací paměti se přidělí dynamicky za běhu. V takovém případě můžete použít speciální verzi `CBookmark` pro kterou nezadáte velikost vyrovnávací paměti. Použijte funkci `GetBookmark` načíst záložky z aktuální záznam, jak je znázorněno v této ukázce kódu:  
  
```cpp  
CTable<CDynamicAccessor> product;  
CBookmark<>              bookmark;  
CDBPropSet propset(DBPROPSET_ROWSET);  
  
propset.AddProperty(DBPROP_BOOKMARKS, true);  

product.Open(session, "Products", &propset);  

product.MoveNext();  

product.GetBookmark(&bookmark);  
```  
  
Informace o podpoře záložky ve zprostředkovatelích najdete v tématu [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md).  
  
## <a name="see-also"></a>Viz také  

[Použití přístupových objektů](../../data/oledb/using-accessors.md)