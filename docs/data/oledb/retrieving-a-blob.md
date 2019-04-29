---
title: Načtení objektu BLOB
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 23bc20355e1e2b17ac20cf975df2ff58d6553ef9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404543"
---
# <a name="retrieving-a-blob"></a>Načtení objektu BLOB

Můžete načíst binární velkých objektů (BLOB) různými způsoby. Můžete použít `DBTYPE_BYTES` k načtení objektu BLOB jako sekvence bajtů nebo můžete použít rozhraní jako `ISequentialStream`. Další informace najdete v tématu [objekty BLOB a objekty OLE](/previous-versions/windows/desktop/ms711511(v=vs.85)) v **OLE DB referenční informace pro programátory**.

Následující kód ukazuje, jak načíst objekt BLOB pomocí `ISequentialStream`. Makro [BLOB_ENTRY](../../data/oledb/blob-entry.md) vám umožní určit rozhraní a příznaky použité pro rozhraní. Po otevření tabulce Kód volá `Read` opakovaně na `ISequentialStream` čtení bajtů z objektu BLOB. Kód volá `Release` k uvolnění rozhraní ukazatele před voláním `MoveNext` zobrazíte další záznam.

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

Použije v následujícím kódu:

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

categories.Open(session, "Categories");

while (categories.MoveNext() == S_OK)
{
   do
   {
      categories.pPicture->Read(myBuffer, 65536, &cb);
      // Do something with the buffer
   } while (cb > 0);
   categories.pPicture->Release();
}
```

Další informace o makra, které zpracovávají data objektů BLOB najdete v tématu **makra Map sloupec** v [makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)<br/>
[Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
