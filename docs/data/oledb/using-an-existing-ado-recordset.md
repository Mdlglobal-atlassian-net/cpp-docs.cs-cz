---
title: Použití existující sady záznamů ADO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 36c74ec0d17c296707334930736d0cf237ecfe7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103561"
---
# <a name="using-an-existing-ado-recordset"></a>Použití existující sady záznamů ADO
Chcete-li kombinovat šablony příjemce technologie OLE DB a objektů Active Data (ADO), použijte ADO k otevření sady záznamů (odpovídající sadě řádků v šablony příjemce technologie OLE DB). Pokud máte sadu záznamů, proveďte postup pro připojení k objektu sady řádků OLE DB:  
  
1.  Volání `QueryInterface` pro `IRowset` a `IAccessor` ukazatele.  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* odkazuje na **IUnknown** objekt sady záznamů ADO.  
  
2.  Připojte k jejich příslušné třídy šablony příjemce technologie OLE DB přistupující objekt a sady řádků.  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)