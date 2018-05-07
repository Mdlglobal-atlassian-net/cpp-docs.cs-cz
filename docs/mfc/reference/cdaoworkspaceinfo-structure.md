---
title: Cdaoworkspaceinfo – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6979124916e8a9cc1dc723008491bababc0322
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo – struktura
`CDaoWorkspaceInfo` Struktura obsahuje informace o pracovním prostoru definované pro přístup k datům přístup objekty (DAO) databáze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoWorkspaceInfo  
{  
    CString m_strName;           // Primary  
    CString m_strUserName;       // Secondary  
    BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Objekt prostoru jedinečné názvy. K načtení hodnoty této vlastnosti přímo, volání objektu querydef [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) – členská funkce. Další informace naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 *m_strUserName*  
 Hodnota, která představuje vlastník objektu pracovního prostoru. Související informace naleznete v tématu "Vlastnost UserName" v nápovědě rozhraní DAO.  
  
 *m_bIsolateODBCTrans*  
 Hodnota, která určuje, zda jsou izolované více transakcí, které zahrnují stejnou databázi ODBC. Další informace najdete v tématu [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Související informace naleznete v tématu "IsolateODBCTrans vlastnost" v nápovědě rozhraní DAO.  
  
## <a name="remarks"></a>Poznámky  
 Pracovní prostor je objekt třídy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Odkazy na primární, sekundární a všechny výše označuje, jak je vrácené informace [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) členské funkce ve třídě `CDaoWorkspace`.  
  
 Načte informace [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) – členská funkce je uložen v `CDaoWorkspaceInfo` struktura. `CDaoWorkspaceInfo` také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoWorkspaceInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)
