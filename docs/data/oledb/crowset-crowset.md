---
title: CRowset::CRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset<TAccessor>::CRowset
- CRowset.CRowset
- ATL::CRowset::CRowset
- ATL::CRowset<TAccessor>::CRowset
- ATL.CRowset.CRowset
- CRowset
- CRowset<TAccessor>.CRowset
- CRowset::CRowset
- ATL.CRowset<TAccessor>.CRowset
dev_langs: C++
helpviewer_keywords: CRowset class, constructor
ms.assetid: 1c6f72e2-f4f4-48dc-957e-038ae8914ba7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad5401daa0032d613ee55519c3973f84a8096746
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetcrowset"></a>CRowset::CRowset
Vytvoří novou `CRowset` objektu a (volitelně) přidruží ji s [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) rozhraní zadanou jako parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      CRowset( );   
CRowset(  
   IRowset* pRowset   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRowset`  
 [v] Ukazatel na `IRowset` rozhraní mají být spojeny s touto třídou.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)