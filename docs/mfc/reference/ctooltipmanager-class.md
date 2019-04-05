---
title: CTooltipManager Class
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: e8b88f2722f5a4379276f13c2ef159aa4d120533
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776502"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager Class

Udržuje běhové informace o popiscích. `CTooltipManager` Třída je instance jednou za každou aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CTooltipManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|Vytvoří ovládací prvek tooltip pro zadaný ovládací prvek typy Windows.|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Odstraní ovládací prvek tooltip.|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Přizpůsobí vzhled ovládacího prvku tooltip pro zadaný ovládací prvek typy Windows.|
|[CTooltipManager::SetTooltipText](#settooltiptext)|Nastaví text a popis pro ovládací prvek tooltip.|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>Poznámky

Použití [cmfctooltipctrl – třída](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, a `CTooltipManager` společně k implementaci vlastní popisy ve vaší aplikaci. Příklad použití těchto tříd popisu tlačítka, najdete v článku [cmfctooltipctrl – třída](../../mfc/reference/cmfctooltipctrl-class.md) tématu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtooltipmanager.h

##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip

Vytvoří ovládací prvek tooltip.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Parametry

*pToolTip*<br/>
[out] Odkaz na ukazatel na popisek. Je nastaven tak, aby odkazoval na nově vytvořený popisek, když funkce vrátí.

*pWndParent*<br/>
[in] Nadřazený popisek.

*nType*<br/>
[in] Typ ovládacího prvku tooltip.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud popisek byl úspěšně vytvořen.

### <a name="remarks"></a>Poznámky

Je nutné volat [CTooltipManager::DeleteToolTip](#deletetooltip) odstranit ToolTip – ovládací prvek, který je předán zpět do *pToolTip*.

[Ctooltipmanager –](../../mfc/reference/ctooltipmanager-class.md) Nastaví zobrazení vizuálu parametry každý popisek vytvoří podle popisu typ, který *nTyp* určuje. Chcete-li změnit parametry pro jeden nebo více typů popisu tlačítka, zavolejte [CTooltipManager::SetTooltipParams](#settooltipparams).

Neplatný popis typy jsou uvedeny v následující tabulce:

|Popis typu|Kategorie ovládacího prvku|Vzorové typy|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Tlačítko.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Záhlaví.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Libovolný ovládací prvek, který není vhodná pro jinou kategorii.|Žádné|
|AFX_TOOLTIP_TYPE_DOCKBAR|Ukotvit panel.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Textové pole.|Žádné|
|AFX_TOOLTIP_TYPE_MINIFRAME|Miniframe.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Plánovač.|Žádné|
|AFX_TOOLTIP_TYPE_RIBBON|Panel pásu karet.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|Ovládací prvek karty.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Panel nástrojů.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Panelu nástrojů.|Žádné|

##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip

Odstraní ovládací prvek tooltip.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Parametry

*pToolTip*<br/>
[out v] Odkaz na ukazatel na popisek, který se má zničit.

### <a name="remarks"></a>Poznámky

Tuto metodu volat pro každou [ctooltipctrl – třída](../../mfc/reference/ctooltipctrl-class.md) , který vytvořil [CTooltipManager::CreateToolTip](#createtooltip). Nadřazený ovládací prvek by měly volat tuto metodu z jeho `OnDestroy` obslužné rutiny. To je nutné správně odebrat popisek z rozhraní framework. Tato metoda nastaví *pToolTip* na hodnotu NULL, před jeho vrácením.

##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams

Přizpůsobení vzhledu ovládacího prvku popisu tlačítka pro zadané typy ovládacích prvků Windows.

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Parametry

*nTypes*<br/>
[in] Určuje typy ovládacích prvků.

*pRTC*<br/>
[in] Modul runtime třídy vlastní popisek.

*pParams*<br/>
[in] Popisek parametrů.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví třídy modulu runtime a počáteční parametry, které [ctooltipmanager –](../../mfc/reference/ctooltipmanager-class.md) používá při vytváření popisů tlačítek. Když ovládacího prvku volá [CTooltipManager::CreateToolTip](#createtooltip) a předá v popisku typ, který je jedním z typů indikován *nTypes*, vytvoří správce popisku ToolTip – ovládací prvek, který je instancí modul runtime třída určená typem *pRTC* a předává parametry určené *pParams* na nový popisek.

Při volání této metody, všichni stávající vlastníci popisek AFX_WM_UPDATETOOLTIPS zpráva a uživatel bude muset znovu vytvořit jejich popisy tlačítek s použitím [CTooltipManager::CreateToolTip](#createtooltip).

*nTypes* může být libovolnou kombinací platný popis typy, které [CTooltipManager::CreateToolTip](#createtooltip) používá nebo to může být AFX_TOOLTIP_TYPE_ALL. Pokud předáte AFX_TOOLTIP_TYPE_ALL, ovlivníte všechny typy popisu tlačítka.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `SetTooltipParams` metodu `CTooltipManager` třídy. Tento fragment kódu je součástí [nakreslit Client sample](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText

Nastaví text a popis pro popis.

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>Parametry

*pTI*<br/>
[in] Ukazatel na objekt TOOLINFO.

*pToolTip*<br/>
[out v] Ukazatel na ovládací prvek tooltip, pro kterou chcete nastavit text a popis.

*nType*<br/>
[in] Určuje typ ovládacího prvku, ke kterému je přidružené tento popisek.

*strText*<br/>
[in] Text, který nastavíte jako text popisku.

*lpszDescr*<br/>
[in] Ukazatel na popis popisku. Může mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Hodnota *nTyp* musí mít stejnou hodnotu jako *nTyp* parametr [CTooltipManager::CreateToolTip](#createtooltip) při vytváření popisek.

##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
void UpdateTooltips();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md)
