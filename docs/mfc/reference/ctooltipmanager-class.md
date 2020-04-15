---
title: CTooltipManager – třída
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
ms.openlocfilehash: 37fcf47b7537e89974a61e6c50c41e164d555678
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365078"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager – třída

Udržuje informace o běhu o popisech. Třída `CTooltipManager` je vytvořena instance jednou na aplikaci.

## <a name="syntax"></a>Syntaxe

```
class CTooltipManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTooltipManager::Vytvořitpopis](#createtooltip)|Vytvoří ovládací prvek popisu pro zadané typy ovládacích prvku systému Windows.|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Odstraní ovládací prvek popisku.|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Přizpůsobí vizuální vzhled ovládacího prvku popisku pro zadané typy ovládacích prvku systému Windows.|
|[CTooltipManager::SetTooltipText](#settooltiptext)|Nastaví text a popis ovládacího prvku popisku.|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>Poznámky

Pomocí [třídy CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) `CMFCToolTipInfo`a `CTooltipManager` společně implementujte vlastní popisky ve vaší aplikaci. Příklad použití těchto tříd popisů naleznete v tématu [třídy CMFCToolTipCtrl.](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtooltipmanager.h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltipManager::Vytvořitpopis

Vytvoří ovládací prvek popisku.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Parametry

*pPopis nástroje*<br/>
[out] Odkaz na ukazatel popisu. Je nastavena tak, aby ukazovala na nově vytvořený popisek, když se funkce vrátí.

*pWndParent*<br/>
[v] Nadřazená popisek.

*nTyp*<br/>
[v] Typ popisku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl popis úspěšně vytvořen.

### <a name="remarks"></a>Poznámky

Chcete-li odstranit ovládací prvek popisu, který je předán zpět v *pToolTip*, je nutné volat [CTooltipManager::DeleteToolTip](#deletetooltip) .

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) nastaví parametry vizuálního zobrazení každého popisku, který vytvoří, na základě typu popisku, který *určuje nType.* Chcete-li změnit parametry pro jeden nebo více typů popisů, zavolejte [CTooltipManager::SetTooltipParams](#settooltipparams).

Platné typy popisů jsou uvedeny v následující tabulce:

|Typ popisku|Kategorie ovládacího prvku|Příklady typů|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Tlačítko.|CmFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Pruh titulků.|CmFCcaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Libovolný ovládací prvek, který neodpovídá jiné kategorii.|Žádné.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Dokovatelné podokno.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Textové pole.|Žádné.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Minirám.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Plánovač.|Žádné.|
|AFX_TOOLTIP_TYPE_RIBBON|Pásový pruh.|CMFCRibbonBar, CMFCRibbonPanelpanel|
|AFX_TOOLTIP_TYPE_TAB|Ovládací prvek karta.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Panel nástrojů.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Beka s nářadím.|Žádné.|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltipManager::DeleteToolTip

Odstraní ovládací prvek popisku.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Parametry

*pPopis nástroje*<br/>
[dovnitř, ven] Odkaz na ukazatel na popisek, který má být zničen.

### <a name="remarks"></a>Poznámky

Volání této metody pro každou [třídu CToolTipCtrl,](../../mfc/reference/ctooltipctrl-class.md) která byla vytvořena [ctooltipmanager::CreateToolTip](#createtooltip). Nadřazený ovládací prvek `OnDestroy` by měl volat tuto metodu z obslužné rutiny. To je nutné správně odebrat popisek z rámce. Tato metoda nastaví *pToolTip* na HODNOTU NULL před vrátí.

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltipManager::SetTooltipParams

Přizpůsobí vzhled ovládacího prvku popisek pro zadané typy ovládacích prvku systému Windows.

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Parametry

*nTypy*<br/>
[v] Určuje typy ovládacích prvku.

*pRTC*<br/>
[v] Runtime třída vlastní popisek.

*pParams*<br/>
[v] Parametry popisku.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví třídu runtime a počáteční parametry, které [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) používá při vytváření popisů. Když ovládací prvek volá [CTooltipManager::CreateToolTip](#createtooltip) a předá v typu popisku, který je jedním z typů označených *nTypes*, správce popisů vytvoří ovládací prvek popisku, který je instancí runtime třídy určené *pRTC* a předá parametry zadané *pParams* do nového popisku.

Při volání této metody všechny existující vlastníky popisků obdrží zprávu AFX_WM_UPDATETOOLTIPS a musí znovu vytvořit jejich popisky pomocí [CTooltipManager::CreateToolTip.](#createtooltip)

*nTypy* mohou být libovolnou kombinací platných typů popisů, které [používá CTooltipManager::CreateToolTip,](#createtooltip) nebo může být AFX_TOOLTIP_TYPE_ALL. Pokud předáte AFX_TOOLTIP_TYPE_ALL, budou ovlivněny všechny typy popisů.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `SetTooltipParams` používat metodu třídy. `CTooltipManager` Tento fragment kódu je součástí [ukázky klienta Draw](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltipManager::SetTooltipText

Nastaví text a popis popisek.

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>Parametry

*Pti*<br/>
[v] Ukazatel na objekt TOOLINFO.

*pPopis nástroje*<br/>
[dovnitř, ven] Ukazatel na ovládací prvek popisku, pro který chcete nastavit text a popis.

*nTyp*<br/>
[v] Určuje typ ovládacího prvku, ke kterému je tento popis přidružen.

*strText*<br/>
[v] Text, který chcete nastavit jako text popisu.

*lpszDescr*<br/>
[v] Ukazatel na popis popisu. Může být NULL.

### <a name="remarks"></a>Poznámky

Hodnota *nType* musí mít stejnou hodnotu jako parametr *nType* [ctooltipmanager::CreateToolTip](#createtooltip) při vytváření popisku.

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTooltipManager::UpdateTooltips

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
void UpdateTooltips();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl – třída](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo – třída](../../mfc/reference/cmfctooltipinfo-class.md)
