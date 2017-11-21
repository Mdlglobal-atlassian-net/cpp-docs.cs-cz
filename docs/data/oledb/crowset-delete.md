---
title: CRowset::Delete | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::Delete
- CRowset.Delete
- CRowset::Delete
- ATL.CRowset.Delete
- ATL::CRowset<TAccessor>::Delete
- CRowset<TAccessor>.Delete
- CRowset<TAccessor>::Delete
- ATL.CRowset<TAccessor>.Delete
dev_langs: C++
helpviewer_keywords: Delete method
ms.assetid: 4feb4f7e-139f-489a-b7d5-ea6ec0058e0f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2fd2839c4d6ff552658024e2b75b3ddba3cf1df1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetdelete"></a>CRowset::Delete
Volání [IRowsetChange::DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx) odstranit na aktuálním řádku ze sady řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT Delete( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CRowset – třída](../../data/oledb/crowset-class.md)