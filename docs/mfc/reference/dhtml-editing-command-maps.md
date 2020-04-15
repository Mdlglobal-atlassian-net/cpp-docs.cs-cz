---
title: Mapy příkazů DHTML pro úpravy
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 62b388eb178be018655ea2b2be00d7321da50335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365820"
---
# <a name="dhtml-editing-command-maps"></a>Mapy příkazů DHTML pro úpravy

Následující makra lze použít k mapování příkazů pro úpravy DHTML v odvozených třídách [CHtmlEditView.](../../mfc/reference/chtmleditview-class.md) Příklad jejich použití naleznete v tématu [HTMLEdit Sample](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Makra mapy mapy pro úpravy příkazů DHTML

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Deklaruje mapu příkazů pro úpravy DHTML ve třídě.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Spustí definici mapy příkazů pro úpravy DHTML v rámci třídy.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Označuje konec mapy příkazů pro úpravy DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Mapuje ID příkazu na příkaz pro úpravy HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Mapuje ID příkazu na příkaz pro úpravy HTML a obslužnou rutinu zprávy.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Mapuje ID příkazu na příkaz pro úpravy HTML a prvek uživatelského rozhraní.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Mapuje ID příkazu na příkaz pro úpravy HTML, obslužnou rutinu zprávy a prvek uživatelského rozhraní.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP

Deklaruje mapu příkazů pro úpravy DHTML ve třídě.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy

### <a name="remarks"></a>Poznámky

Toto makro má být použito v definici tříd odvozených z [CHtmlEditView.](../../mfc/reference/chtmleditview-class.md)

Pomocí [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) k implementaci mapy.

### <a name="example"></a>Příklad

Viz [HTMLEdit ukázka](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxhtml.h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP

Spustí definici mapy příkazů pro úpravy DHTML v rámci třídy.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy obsahující mapu příkazů pro úpravy DHTML. Tato třída by měla být odvozena přímo nebo nepřímo z [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) a zahrnout [makro DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) v rámci definice třídy.

### <a name="remarks"></a>Poznámky

Přidejte do třídy mapu příkazů pro úpravy DHTML a mapujte příkazy uživatelského rozhraní na příkazy pro úpravy HTML.

Umístěte makro BEGIN_DHTMLEDITING_CMDMAP do souboru implementace třídy (.cpp) následované [makry DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) pro příkazy, které má třída mapovat (například z ID_EDIT_CUT do IDM_CUT). Pomocí [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) makra označte konec mapy událostí.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxhtml.h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP

Označuje konec mapy příkazů pro úpravy DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Poznámky

Používejte ve spojení s [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Příklad

Viz [HTMLEdit ukázka](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxhtml.h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY

Mapuje ID příkazu na příkaz pro úpravy HTML.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Příkaz pro úpravy HTML, na který *cmdID mapuje* (například IDM_COPY).

### <a name="example"></a>Příklad

Viz [HTMLEdit ukázka](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC

Mapuje ID příkazu na příkaz pro úpravy HTML a obslužnou rutinu zprávy.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Příkaz pro úpravy HTML, na který *cmdID mapuje* (například IDM_COPY).

*member_func_name*<br/>
Název funkce obslužné rutiny zprávy, na kterou je příkaz mapován.

### <a name="example"></a>Příklad

Viz [HTMLEdit ukázka](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxhtml.h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE

Mapuje ID příkazu na příkaz pro úpravy HTML a prvek uživatelského rozhraní.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Příkaz pro úpravy HTML, na který *cmdID mapuje* (například IDM_COPY).

*elemTyp*<br/>
Typ prvku uživatelského rozhraní; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX nebo AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Příklad

Viz [HTMLEdit ukázka](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Mapuje ID příkazu na příkaz pro úpravy HTML, obslužnou rutinu zprávy a prvek uživatelského rozhraní.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Příkaz pro úpravy HTML, na který *cmdID mapuje* (například IDM_COPY).

*member_func_name*<br/>
Název funkce obslužné rutiny zprávy, na kterou je příkaz mapován.

*elemTyp*<br/>
Typ prvku uživatelského rozhraní; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX nebo AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Příklad

Viz [HTMLEdit ukázka](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxhtml.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
