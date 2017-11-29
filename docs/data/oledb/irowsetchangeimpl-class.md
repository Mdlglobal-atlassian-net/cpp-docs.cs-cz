---
title: "IRowsetChangeImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
dev_langs: C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4dc31fc66f28f6fd9a8d9e9bc7122bf2aa7b2b73
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl – třída
Implementace šablony technologie OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) rozhraní ve specifikaci OLE DB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >   
>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída odvozená z `IRowsetChangeImpl`.  
  
 `Storage`  
 Záznamu uživatele.  
  
 `BaseInterface`  
 Základní třída pro rozhraní, jako například `IRowsetChange`.  
  
 `RowClass`  
 Jednotky úložiště pro popisovač řádku.  
  
 `MapClass`  
 Jednotky úložiště pro všechny popisovačů řádků uchovávat zprostředkovatelem.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Metody rozhraní (používá se s IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|Odstraní řádky ze sady řádků.|  
|[Insertrow –](../../data/oledb/irowsetchangeimpl-insertrow.md)|Vloží řádek do sady řádků.|  
|[SetData –](../../data/oledb/irowsetchangeimpl-setdata.md)|Nastaví hodnoty dat v jedné nebo více sloupců.|  
  
### <a name="implementation-method-callback"></a>Implementace metody (zpětného volání)  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|Overidden poskytovatelem potvrdit data do jeho úložiště.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je zodpovědná za operace okamžitou zápisu do datového úložiště. "Okamžitou" znamená, že pokud koncový uživatel (uživatel používající příjemce) neprovede žádné změny, tyto změny hned přenosu dat uložit (a nelze vrátit zpět).  
  
 `IRowsetChangeImpl`implementuje OLE DB `IRowsetChange` rozhraní, která umožňuje aktualizaci hodnot sloupců v existujících řádků, odstranění řádků a vkládání nových řádků.  
  
 Šablony OLE DB implementace podporuje všechny základní metody (`SetData`, `InsertRow`, a `DeleteRows`).  
  
> [!IMPORTANT]
>  Důrazně doporučujeme, abyste si přečetli následující dokumentace před pokusem o implementovat poskytovatele:  
  
-   [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Kapitoly 6 *referenční příručka programátora prostředí OLE DB*  
  
-   Informace v tématu Jak `RUpdateRowset` třída se používá v ukázce UpdatePV  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)