---
title: IRowsetImpl::m_bReset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
dev_langs:
- C++
helpviewer_keywords:
- m_bReset
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ca38b0fa56f901d18e90d3305c92cc097452369
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
Bitový příznak, který používá k určení, pokud pozice kurzoru je definována v sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud příjemce volá [GetNextRows –](../../data/oledb/irowsetimpl-getnextrows.md) s jako záporné `lOffset` nebo *cRows* a `m_bReset` má hodnotu true, `GetNextRows` přesune na konec objektu sady řádků. Pokud `m_bReset` je nastavena hodnota false, příjemci přijímá chybový kód, v souladu se specifikací OLE DB. `m_bReset` Získá příznak nastaven na hodnotu **true** při prvním vytvoření sady řádků a když příjemce volá [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Získá nastavit na **false** při volání `GetNextRows`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)