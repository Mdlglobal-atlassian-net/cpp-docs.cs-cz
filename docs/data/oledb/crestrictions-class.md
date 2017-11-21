---
title: "CRestrictions – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
dev_langs: C++
helpviewer_keywords: CRestrictions class
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88ba3c853bbd12c1512dbb8c70c0941718b1396f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crestrictions-class"></a>CRestrictions – třída
Obecná třída, která můžete nastavit omezení pro sady řádků schématu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <   
   class T,   
   short nRestrictions,   
   const GUID* pguid   
>  
class CRestrictions : public CSchemaRowset <   
   T,   
   nRestrictions   
>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída používaná pro přistupující objekt.  
  
 `nRestrictions`  
 Počet sloupců omezení pro sadu řádků schématu.  
  
 `pguid`  
 Ukazatel na identifikátor GUID schématu.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Otevřete](../../data/oledb/crestrictions-open.md)|Vrátí výsledek nastavena podle uživatelem zadané omezení.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldbsch.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)