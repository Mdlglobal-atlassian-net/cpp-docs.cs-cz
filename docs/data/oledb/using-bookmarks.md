---
title: Použití záložek
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 579e67151858904e877a34bf30467e3cb97fe2c4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028490"
---
# <a name="using-bookmarks"></a>Použití záložek

Před otevřením v sadě řádků musí sdělte poskytovateli, že chcete používat záložky. Chcete-li to provést, nastavte `DBPROP_BOOKMARKS` vlastnost **true** ve vaší vlastnost nastavit. Zprostředkovatel načte záložky jako sloupec nula, je nutné použít speciální makro BOOKMARK_ENTRY a `CBookmark` třídy, pokud používáte statického následovníka. `CBookmark` je třída šablony, kde je argument délku vyrovnávací paměti záložek v bajtech. Délka vyrovnávací paměti vyžadované pro záložku závisí na poskytovateli. Pokud používáte zprostředkovatele ODBC OLE DB, jak je znázorněno v následujícím příkladu, musí být vyrovnávací paměti 4 bajty.

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

Použije v následujícím kódu:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Pokud používáte `CDynamicAccessor`, vyrovnávací paměti je nastavení dynamicky za běhu. V takovém případě můžete použít speciální verzi `CBookmark` pro které nechcete zadat velikost vyrovnávací paměti. Použijte funkci `GetBookmark` načíst záložky z aktuální záznam, jak je znázorněno v této ukázce kódu:

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

Informace o podpoře záložky ve zprostředkovatelích najdete v tématu [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)