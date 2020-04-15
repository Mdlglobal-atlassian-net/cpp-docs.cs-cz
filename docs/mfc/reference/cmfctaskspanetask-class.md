---
title: Třída úloh CMFCTasksPane
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
ms.openlocfilehash: 49fccdf161da7deb1fd88a12a107df40bafdae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375871"
---
# <a name="cmfctaskspanetask-class"></a>Třída úloh CMFCTasksPane

Třída `CMFCTasksPaneTask` je pomocná třída, která představuje úkoly pro ovládací prvek podokna úloh [(CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). Objekt úkolu představuje položku ve skupině úloh ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Každá úloha může mít příkaz, který provede rozhraní, když uživatel klikne na úlohu a ikonu, která se zobrazí vlevo od názvu úkolu.

## <a name="syntax"></a>Syntaxe

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTaskTask CMFCTasksPaneTask CMFCTasksPaneTask CMFCTasksPaneTask CMFCTasksPaneTask CMFCTasksPaneTask](#cmfctaskspanetask)|Vytvoří a inicializuje `CMFCTasksPaneTask` objekt.|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Určuje data usnadnění pro aktuální úkol.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Určuje, zda je okno úkolu automaticky zničeno.|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Určuje, zda rámec nakreslí popisek úkolu tučným písmem.|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Obsahuje uživatelem definovaná data, která rozhraní framework přidružuje k úkolu. Pokud úkol nenastaví žádná přidružená data, je nastavena na nulu.|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Popisovač okna úkolu.|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|Index v seznamu obrázků, které rozhraní zobrazuje vedle úkolu.|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|Výška okna úkolu. Pokud úkol nemá žádné okno úkolu, je tato hodnota nulová.|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Ukazatel `CMFCTasksPaneTaskGroup` na, ke kterému tento úkol patří.|
|[CMFCTasksPaneTask::m_rect](#m_rect)|Určuje ohraničovací obdélník úlohy.|
|[CMFCTasksPaneTask::m_strName](#m_strname)|Název úlohy|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Určuje ID příkazu, který provede rozhraní, když uživatel klepne na úlohu. Pokud tato hodnota není platné ID příkazu, úloha je považována za jednoduchý popisek.|

## <a name="remarks"></a>Poznámky

Následující obrázek znázorňuje skupinu úkolů, která obsahuje tři úkoly:

![Skupina úkolů, rozbalená](../../mfc/reference/media/nexttaskgrpexpand.png "Skupina úkolů, rozbalená")

> [!NOTE]
> Pokud úloha nemá platné ID příkazu, je považována za jednoduchý popisek.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCTasksPaneTaskTaskTaskTaskTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxTasksPane.h

## <a name="cmfctaskspanetaskcmfctaskspanetask"></a><a name="cmfctaskspanetask"></a>CMFCTasksPaneTask::CMFCTasksPaneTaskTask CMFCTasksPaneTask CMFCTasksPaneTask CMFCTasksPaneTask CMFCTasksPaneTask CMFCTasksPaneTask

Vytvoří a inicializuje `CMFCTasksPaneTask` objekt.

```
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,
    LPCTSTR lpszName,
    int nIcon,
    UINT uiCommandID,
    DWORD dwUserData = 0,
    HWND hwndTask = NULL,
    BOOL bAutoDestroyWindow = FALSE,
    int nWindowHeight = 0);
```

### <a name="parameters"></a>Parametry

*pSkupina*<br/>
Určuje [skupinu CMFCTasksPaneTaskGroup,](../../mfc/reference/cmfctaskspanetaskgroup-class.md) do které úloha patří.

*název lpsz*<br/>
Určuje název úlohy.

*nIkona*<br/>
Určuje index obrazu úkolu v seznamu obrázků.

*uiCommandID*<br/>
Určuje ID příkazu, který je proveden po klepnutí na úlohu.

*dwUserData*<br/>
Uživatelem definovaná data.

*hwndÚkol*<br/>
Určuje popisovač okna úlohy.

*bAutoDestroyWindow*<br/>
Pokud true, okno úkolu bude zničenautomaticky.

*nVýška okna*<br/>
Určuje výšku okna úkolu.

### <a name="remarks"></a>Poznámky

## <a name="cmfctaskspanetaskm_bautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCTasksPaneTask::m_bAutoDestroyWindow

Určuje, zda je okno úkolu automaticky zničeno.

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Poznámky

Nastavte hodnotu TRUE, chcete-li určit, že okno úkolu ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) by mělo být automaticky zničeno; jinak NEPRAVDA.

## <a name="cmfctaskspanetaskm_bisbold"></a><a name="m_bisbold"></a>CMFCTasksPaneTask::m_bIsBold

Určuje, zda je popisek úkolu nakreslen tučným písmem.

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na HODNOTU TRUE, aby se zobrazil tučný text popisku úkolu.

## <a name="cmfctaskspanetaskm_dwuserdata"></a><a name="m_dwuserdata"></a>CMFCTasksPaneTask::m_dwUserData

Obsahuje uživatelem definovaná data, která jsou přidružena k úloze. Nastavte na nulu, pokud k úkolu nejsou přidružena žádná data.

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Poznámky

## <a name="cmfctaskspanetaskm_hwndtask"></a><a name="m_hwndtask"></a>CMFCTasksPaneTask::m_hwndTask

Popisovač okna úkolu.

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Poznámky

Chcete-li přidat okno úkolu, zavolejte [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).

## <a name="cmfctaskspanetaskm_nicon"></a><a name="m_nicon"></a>CMFCTasksPaneTask::m_nIcon

Pozice indexu v seznamu obrázků, která identifikuje obrázek, který je zobrazen vedle zadané úlohy.

```
int m_nIcon;
```

### <a name="remarks"></a>Poznámky

Seznam obrázků je nastaven [cmfctaskspane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).

Pokud `m_nIcon` chcete úkol zobrazit bez obrázku, nastavte na -1.

## <a name="cmfctaskspanetaskm_nwindowheight"></a><a name="m_nwindowheight"></a>CMFCTasksPaneTask::m_nWindowHeight

Výška okna úkolu. Pokud úkol nemá žádné okno úkolu, je tato hodnota nulová.

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Poznámky

## <a name="cmfctaskspanetaskm_pgroup"></a><a name="m_pgroup"></a>CMFCTasksPaneTask::m_pGroup

Ukazatel na [skupinu CMFCTasksPaneTaskGroup,](../../mfc/reference/cmfctaskspanetaskgroup-class.md) do které tento úkol patří.

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Poznámky

Každý úkol musí mít nadřazenou skupinu. Skupiny přidáte do podokna úloh voláním [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).

## <a name="cmfctaskspanetaskm_rect"></a><a name="m_rect"></a>CMFCTasksPaneTask::m_rect

Určuje ohraničovací obdélník úlohy.

```
CRect m_rect;
```

### <a name="remarks"></a>Poznámky

Tato hodnota je vypočtena rámci při nakreslené úlohy.

## <a name="cmfctaskspanetaskm_strname"></a><a name="m_strname"></a>CMFCTasksPaneTask::m_strName

Název úlohy

```
CString m_strName;
```

### <a name="remarks"></a>Poznámky

## <a name="cmfctaskspanetaskm_uicommandid"></a><a name="m_uicommandid"></a>CMFCTasksPaneTask::m_uiCommandID

Určuje ID příkazu, který je proveden, když uživatel klepne na úlohu. Pokud tato hodnota není platné ID příkazu, úloha je považována za jednoduchý popisek.

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Poznámky

## <a name="cmfctaskspanetasksetaccdata"></a><a name="setaccdata"></a>CMFCTasksPaneTask::SetACCData

Určuje data usnadnění pro aktuální úkol.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
[v] Představuje nadřazené okno aktuální úlohy.

*Dat*<br/>
[out] Objekt typu, `CAccessibilityData` který je naplněn daty usnadnění aktuální úlohy.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byl parametr *dat* úspěšně naplněn daty usnadnění aktuální úlohy; jinak NEPRAVDA.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)
