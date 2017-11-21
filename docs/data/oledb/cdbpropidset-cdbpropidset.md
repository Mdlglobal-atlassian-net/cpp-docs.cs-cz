---
title: CDBPropIDSet::CDBPropIDSet | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
dev_langs: C++
helpviewer_keywords: CDBPropIDSet class, constructor
ms.assetid: e68cc20e-fce2-4cc1-9e9d-05c542334cc8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 310d5eb22c2fb57b001a9a5e40599c163358319f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdbpropidsetcdbpropidset"></a>CDBPropIDSet::CDBPropIDSet
Konstruktor Inicializuje **rgProperties**, **cProperties**a (volitelně) **guidPropertySet** pole [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      CDBPropIDSet(  
   const GUID& guid   
);  
CDBPropIDSet(   
   const CDBPropIDSet& propidset    
);  
CDBPropIDSet( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 [v] Identifikátor GUID použitý k inicializaci **guidPropertySet** pole.  
  
 *propidset*  
 [v] Jiné `CDBPropIDSet` objekt pro vytváření kopie.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDBPropIDSet – třída](../../data/oledb/cdbpropidset-class.md)   
 [CDBPropIDSet::SetGUID](../../data/oledb/cdbpropidset-setguid.md)