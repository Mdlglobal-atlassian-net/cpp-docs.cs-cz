---
title: CEnumerator::Find | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
dev_langs:
- C++
helpviewer_keywords:
- Find method
ms.assetid: 69a153af-d6c3-40fd-9018-27c7d2f344c6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 863832f41c866764883336c7de76fa343eb1cbac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cenumeratorfind"></a>CEnumerator::Find
Vyhledá zadaný název mezi dostupných zprostředkovatelů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *szSearchName*  
 [v] Název pro vyhledávání.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud název byl nalezen. V opačném **false**.  
  
## <a name="remarks"></a>Poznámky  
 Tento název se mapuje **SOURCES_NAME** členem [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CEnumerator – třída](../../data/oledb/cenumerator-class.md)