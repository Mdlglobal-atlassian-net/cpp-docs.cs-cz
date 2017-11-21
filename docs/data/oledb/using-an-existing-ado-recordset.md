---
title: "Použití existující sady záznamů ADO | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6331bd40cd65fb7b367a3958aa4fb00a2f123958
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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