---
title: Použití záložek
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 5a4a2d65ba7367b5568603b5f08a07c6d85cc4a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209310"
---
# <a name="using-bookmarks"></a>Použití záložek

Před otevřením sady řádků je nutné sdělit poskytovateli, že chcete použít záložky. Chcete-li to provést, nastavte vlastnost `DBPROP_BOOKMARKS` na **hodnotu true** v sadě vlastností. Zprostředkovatel načte záložky jako sloupec nula, takže je nutné použít speciální BOOKMARK_ENTRY makra a `CBookmark` třídu, pokud používáte statický přistupující objekt. `CBookmark` je třída šablony, kde argument je délka v bajtech vyrovnávací paměti záložky. Délka vyrovnávací paměti vyžadované záložkou závisí na poskytovateli. Pokud používáte poskytovatele OLE DB ODBC, jak je znázorněno v následujícím příkladu, vyrovnávací paměť musí být 4 bajty.

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

Pak se používá v následujícím kódu:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Použijete-li `CDynamicAccessor`, vyrovnávací paměť je dynamicky nastavena v době běhu. V takovém případě můžete použít specializovanou verzi `CBookmark`, pro kterou nezadáte délku vyrovnávací paměti. Použijte funkci `GetBookmark` k načtení záložky z aktuálního záznamu, jak je znázorněno v této ukázce kódu:

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

Informace o podpoře záložek v poskytovatelích najdete v tématu [Podpora poskytovatelů pro záložky](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
