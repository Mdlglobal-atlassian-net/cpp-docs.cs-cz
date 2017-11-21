---
title: IRowsetImpl::m_bReset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
dev_langs: C++
helpviewer_keywords: m_bReset
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4323d92398ea4d47410a2b5a3aad08972628634d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
Bitový příznak, který používá k určení, pokud pozice kurzoru je definována v sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud příjemce volá [GetNextRows –](../../data/oledb/irowsetimpl-getnextrows.md) s jako záporné `lOffset` nebo *cRows* a `m_bReset` má hodnotu true, `GetNextRows` přesune na konec objektu sady řádků. Pokud `m_bReset` je nastavena hodnota false, příjemci přijímá chybový kód, v souladu se specifikací OLE DB. `m_bReset` Získá příznak nastaven na hodnotu **true** při prvním vytvoření sady řádků a když příjemce volá [IRowsetImpl::RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Získá nastavit na **false** při volání `GetNextRows`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)