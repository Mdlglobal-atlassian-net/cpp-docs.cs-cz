---
title: "CBookmark – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 08ab7ca180433861be2dc9081dd991dbeb89642d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cbookmark-class"></a>CBookmark – třída
Obsahuje hodnotu záložku v jeho vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### <a name="parameters"></a>Parametry  
 `nSize`  
 Velikost vyrovnávací paměti záložek v bajtech. Když `nSize` rovná nule, vyrovnávací paměti záložek se dynamicky vytvoří za běhu.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|Konstruktor|  
|[Getbuffer –](../../data/oledb/cbookmark-getbuffer.md)|Načte ukazatele do vyrovnávací paměti.|  
|[Getsize –](../../data/oledb/cbookmark-getsize.md)|Získá velikost vyrovnávací paměti v bajtech.|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|Nastaví hodnotu záložky.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../../data/oledb/cbookmark-operator-equal.md)|Přiřadí jeden `CBookmark` třída do jiného.|  
  
## <a name="remarks"></a>Poznámky  
 **CBookmark\<0 >** je specializace šablony z `CBookmark`; jeho vyrovnávací paměti je vytvořen dynamicky za běhu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)