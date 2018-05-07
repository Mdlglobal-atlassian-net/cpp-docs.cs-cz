---
title: Načtení objektu BLOB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 420e863fcd5d4c666bf8e9a25a2f0f53e726c871
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-a-blob"></a>Načtení objektu BLOB
Můžete načíst binární rozsáhlý objekt (binární rozsáhlý OBJEKT) různými způsoby. Můžete použít **DBTYPE_BYTES** k načtení objektu BLOB jako sekvenci bajtů, nebo použít rozhraní jako `ISequentialStream`. Další informace najdete v tématu [objekty BLOB a objekty OLE](https://msdn.microsoft.com/en-us/library/ms711511.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
 Následující kód ukazuje, jak načíst objekt BLOB pomocí `ISequentialStream`. Makro [BLOB_ENTRY](../../data/oledb/blob-entry.md) vám umožní určit rozhraní a příznaky použité pro rozhraní. Po otevření v tabulce, kód zavolá **čtení** opakovaně na `ISequentialStream` čtení bajtů z objektu BLOB. Volání kódu **verze** k uvolnění ukazatele rozhraní před voláním `MoveNext` k získání dalšího záznamu.  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories>> categories;  
ULONG          cb;  
BYTE            myBuffer[65536];  
  
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
  
 Další informace o makra, které zpracovávají data objektů BLOB, najdete v části "Makra mapy sloupec" v [makra a globální funkce pro šablony příjemce technologie OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)   
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)