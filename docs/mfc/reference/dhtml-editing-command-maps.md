---
title: Mapy příkazů DHTML pro úpravy
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 1f84a56876f1108e9b02d44f6ef0dec50f065c57
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278259"
---
# <a name="dhtml-editing-command-maps"></a>Mapy příkazů DHTML pro úpravy

Následující makra lze použít k mapování DHTML pro úpravy příkazy v [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-odvozené třídy. Příklad použití, naleznete v tématu [HTMLEdit ukázka](../../visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Makra Map DHTML pro úpravy příkaz

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Deklaruje DHTML pro úpravy příkaz mapu ve třídě.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Spustí definici DHTML pro úpravy příkaz mapy v rámci třídy.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Označuje konec DHTML pro úpravy mapování příkazu.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Mapuje ID příkazu pro příkaz pro úpravy HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Mapuje ID příkazu příkazu úprav jazyka HTML a obslužné rutiny zpráv.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Mapuje ID příkazu příkazu úprav jazyka HTML a prvek uživatelského rozhraní.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Mapuje ID příkazu pro příkaz, obslužné rutiny zpráv a prvek uživatelského rozhraní pro úpravy HTML.|

##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP

Deklaruje DHTML pro úpravy příkaz mapu ve třídě.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*className*<br/>
Název třídy.

### <a name="remarks"></a>Poznámky

Toto makro se má použít v definici [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-odvozené třídy.

Použití [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) k implementaci na mapě.

### <a name="example"></a>Příklad

Zobrazit [HTMLEdit ukázka](../../visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Header** afxhtml.h

##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP

Spustí definici DHTML pro úpravy příkaz mapy v rámci třídy.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*className*<br/>
Název třídy obsahující mapování DHTML pro úpravy příkazu. Tato třída musí být odvozený přímo nebo nepřímo z: [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) a zahrnout [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) – makro v rámci dané definice třídy.

### <a name="remarks"></a>Poznámky

Přidáte mapu DHTML pro úpravy příkaz do vaší třídy k mapování příkazů uživatelského rozhraní pro příkazy pro úpravy HTML.

Umístit BEGIN_DHTMLEDITING_CMDMAP – makro v souboru implementace (.cpp) třídy následovaný [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) makra pro příkazy třídy je mapovat (např. z id_edit_cut – k IDM_CUT). Použití [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) – makro konec mapa událostí.

### <a name="requirements"></a>Požadavky

  **Header** afxhtml.h

##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP

Označuje konec DHTML pro úpravy mapování příkazu.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Poznámky

Použití ve spojení s [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Příklad

Zobrazit [HTMLEdit ukázka](../../visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Header** afxhtml.h

##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY

Mapuje ID příkazu pro příkaz pro úpravy HTML.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například id_edit_copy –).

*dhtmlcmdID*<br/>
Příkaz, ke kterému pro úpravu kódu HTML *cmdID* mapuje (například IDM_COPY).

### <a name="example"></a>Příklad

Zobrazit [HTMLEdit ukázka](../../visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Header** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC

Mapuje ID příkazu příkazu úprav jazyka HTML a obslužné rutiny zpráv.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například id_edit_copy –).

*dhtmlcmdID*<br/>
Příkaz, ke kterému pro úpravu kódu HTML *cmdID* mapuje (například IDM_COPY).

*member_func_name*<br/>
Název funkce obslužná rutina zprávy, ke které je mapován tento příkaz.

### <a name="example"></a>Příklad

Zobrazit [HTMLEdit ukázka](../../visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Header** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE

Mapuje ID příkazu příkazu úprav jazyka HTML a prvek uživatelského rozhraní.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například id_edit_copy –).

*dhtmlcmdID*<br/>
Příkaz, ke kterému pro úpravu kódu HTML *cmdID* mapuje (například IDM_COPY).

*elemType*<br/>
Typ prvku uživatelského rozhraní; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX nebo AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Příklad

Zobrazit [HTMLEdit ukázka](../../visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Header** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Mapuje ID příkazu pro příkaz, obslužné rutiny zpráv a prvek uživatelského rozhraní pro úpravy HTML.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
ID příkazu (například id_edit_copy –).

*dhtmlcmdID*<br/>
Příkaz, ke kterému pro úpravu kódu HTML *cmdID* mapuje (například IDM_COPY).

*member_func_name*<br/>
Název funkce obslužná rutina zprávy, ke které je mapován tento příkaz.

*elemType*<br/>
Typ prvku uživatelského rozhraní; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX nebo AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Příklad

Zobrazit [HTMLEdit ukázka](../../visual-cpp-samples.md).

### <a name="requirements"></a>Požadavky

  **Header** afxhtml.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
