---
title: CDaoWorkspaceInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253627"
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

*m_strName*<br/>
Jedinečné názvy objektu pracovního prostoru. K načtení hodnoty této vlastnosti přímo, volání objektu querydef [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) členskou funkci. Další informace naleznete v tématu "Název vlastnosti" v nápovědě k DAO.

*m_strUserName*<br/>
Hodnota, která představuje vlastníka pracovního prostoru objektu. Související informace naleznete v tématu "Vlastnost UserName" v nápovědě k DAO.

*m_bIsolateODBCTrans*<br/>
Hodnota, která určuje, zda jsou izolované více transakcí, které se týkají stejné databáze ODBC. Další informace najdete v tématu [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Související informace naleznete v tématu "IsolateODBCTrans vlastnost" v nápovědě k DAO.

## <a name="remarks"></a>Poznámky

Pracovní prostor je objekt třídy [cdaoworkspace –](../../mfc/reference/cdaoworkspace-class.md). Odkazy na primární, sekundární a všechny výše určit, jak vrácené informace [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) členské funkce ve třídě `CDaoWorkspace`.

Načte informace [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) členská funkce je uložen v `CDaoWorkspaceInfo` struktury. `CDaoWorkspaceInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoWorkspaceInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)
