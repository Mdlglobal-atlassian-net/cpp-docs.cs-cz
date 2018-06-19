---
title: IRowsetImpl::m_bReset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9aec38e3cf7e9a58c4fe99d06f35ae55cfdf81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102004"
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