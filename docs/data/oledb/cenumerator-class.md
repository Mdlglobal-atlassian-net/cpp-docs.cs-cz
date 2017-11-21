---
title: "CEnumerator – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CEnumerator
dev_langs: C++
helpviewer_keywords: CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 856356117161a0c9e3588732faf01c3a663b6a9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cenumerator-class"></a>CEnumerator – třída
Používá objekt enumerator OLE DB, který zveřejňuje [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) rozhraní vrátí sadu řádků, které popisují všechny zdroje dat a výčty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Najít](../../data/oledb/cenumerator-find.md)|Hledání prostřednictvím (zdroje dat) dostupných zprostředkovatelů vyhledávání pro jednu se zadaným názvem.|  
|[Getmoniker –](../../data/oledb/cenumerator-getmoniker.md)|Načte `IMoniker` rozhraní pro záznam na aktuální záznam.|  
|[Otevřete](../../data/oledb/cenumerator-open.md)|Otevře enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat **ISourcesRowset** data nepřímo z této třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:**také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)