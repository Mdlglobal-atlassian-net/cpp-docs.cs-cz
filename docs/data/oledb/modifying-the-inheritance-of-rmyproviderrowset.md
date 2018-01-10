---
title: "Úprava dědičnosti třídy RMyProviderRowset | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ff6e953bf706e0e8767fe6f97fe1d31b70431d08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>Úprava dědičnosti třídy RMyProviderRowset
Chcete-li přidat `IRowsetLocate` rozhraní v příkladu jednoduchého zprostředkovatele pouze pro čtení, změňte dědičnost **RMyProviderRowset**. Na začátku **RMyProviderRowset** dědí z `CRowsetImpl`. Je potřeba upravit tak, aby dědí **CRowsetBaseImpl**.  
  
 Chcete-li to provést, vytvořte novou třídu, `CMyRowsetImpl`, v souboru MyProviderRS.h:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage> >  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate > >  
{  
...  
};  
```  
  
 Nyní upravte mapu rozhraní modelu COM v souboru MyProviderRS.h být následujícím způsobem:  
  
```  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Tím se vytvoří mapa rozhraní modelu COM, která informuje `CMyRowsetImpl` volat **QueryInterface** pro oba `IRowset` a `IRowsetLocate` rozhraní. Získat všechny ostatní sady řádků implementace třídy, mapa odkazuje `CMyRowsetImpl` třída zpět do **CRowsetBaseImpl** třídy definují šablony technologie OLE DB, mapa používá makro COM_INTERFACE_ENTRY_CHAIN, které sděluje Šablony technologie OLE DB kontrola knihovny COM mapování v **CRowsetBaseImpl** v reakci `QueryInterface` volání.  
  
 Nakonec propojí `RAgentRowset` k `CMyRowsetBaseImpl` změnou `RAgentRowset` dědění z `CMyRowsetImpl`, a to takto:  
  
```  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
 `RAgentRowset`Teď můžete použít `IRowsetLocate` rozhraní s využitím zbytek implementace pro třídu sady řádků.  
  
 Když to uděláte, můžete [dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)