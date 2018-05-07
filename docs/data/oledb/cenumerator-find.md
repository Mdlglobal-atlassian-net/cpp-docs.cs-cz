---
title: CEnumerator::Find | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2466127dab53fa6646a4f149400e4318aed59970
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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