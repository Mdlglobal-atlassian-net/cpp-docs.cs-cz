---
title: CMouseManager – třída
ms.date: 11/04/2016
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
ms.openlocfilehash: d05a2e186f001a69310e99cec013193a4d1bff3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319725"
---
# <a name="cmousemanager-class"></a>CMouseManager – třída

Umožňuje uživateli přidružit různé příkazy k určitému objektu [CView,](../../mfc/reference/cview-class.md) když uživatel poklepe uvnitř tohoto zobrazení.

## <a name="syntax"></a>Syntaxe

```
class CMouseManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Přidá `CView` objekt do dialogového okna **Přizpůsobení.** Dialogové okno **Přizpůsobení** umožňuje uživateli přidružit poklepání pomocí příkazu pro každé z uvedených zobrazení.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Vrátí příkaz, který je proveden, když uživatel poklepe uvnitř poskytnutého zobrazení.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Vrátí ikonu přidruženou k ID zadaným zobrazením.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Vrátí ID zobrazení přidružené k zadaný název zobrazení.|
|[CMouseManager::GetViewNames](#getviewnames)|Načte seznam všech přidaných názvů zobrazení.|
|[CMouseManager::LoadState](#loadstate)|Načte `CMouseManager` stav z registru systému Windows.|
|[CMouseManager::Uložitstav](#savestate)|Zapíše `CMouseManager` stav do registru systému Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Přidruží zadaný příkaz a zadaný pohled.|

## <a name="remarks"></a>Poznámky

Třída `CMouseManager` udržuje kolekci `CView` objektů. Každé zobrazení je označeno názvem a ID. Tato zobrazení jsou zobrazena v dialogovém okně **Přizpůsobení.** Uživatel může změnit příkaz, který je přidružen k libovolnému zobrazení, prostřednictvím dialogového okna **Přizpůsobení.** Přidružený příkaz je proveden, když uživatel v tomto zobrazení poklekne. Chcete-li to podporovat z hlediska kódování, musíte zpracovat zprávu WM_LBUTTONDBLCLK a zavolat funkci [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) v kódu pro tento `CView` objekt..

Objekt byste neměli vytvářet `CMouseManager` ručně. Bude vytvořen v rámci vaší aplikace. Bude také automaticky zničen, když uživatel ukončí aplikaci. Chcete-li získat ukazatel na správce myši pro vaši aplikaci, volejte [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmousemanager.h

## <a name="cmousemanageraddview"></a><a name="addview"></a>CMouseManager::AddView

Zaregistruje [cview](../../mfc/reference/cview-class.md) objekt s [CMouseManager třídy](../../mfc/reference/cmousemanager-class.md) pro podporu chování vlastní myši.

```
BOOL AddView(
    int iViewId,
    UINT uiViewNameResId,
    UINT uiIconId = 0);

BOOL AddView(
    int iId,
    LPCTSTR lpszViewName,
    UINT uiIconId = 0);
```

### <a name="parameters"></a>Parametry

*iViewId*<br/>
[v] ID zobrazení.

*uiViewNameResd*<br/>
[v] ID řetězce prostředku, které odkazuje na název zobrazení.

*uiIconId*<br/>
[v] ID ikony zobrazení.

*Iid*<br/>
[v] ID zobrazení.

*lpszViewName*<br/>
[v] Název zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Chcete-li podporovat vlastní chování myši, musí `CMouseManager` být zobrazení registrováno s objektem. Libovolný objekt odvozený `CView` z třídy lze zaregistrovat u správce myši. Řetězec a ikona přidružené k zobrazení jsou zobrazeny na kartě **Myš** v dialogovém okně **Přizpůsobit.**

Je odpovědností programátora vytvořit a udržovat ID zobrazení, jako je *iViewId* a *iId*.

Další informace o tom, jak zajistit vlastní chování myši, naleznete v [tématu Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst `CMouseManager` ukazatel na `CWinAppEx::GetMouseManager` objekt pomocí `AddView` metody `CMouseManager` a metody ve třídě. Tento fragment kódu je součástí [ukázky kolekce stavu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

## <a name="cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand

Vrátí příkaz, který je proveden, když uživatel poklepe uvnitř poskytnutého zobrazení.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] ID zobrazení.

### <a name="return-value"></a>Návratová hodnota

Identifikátor příkazu, pokud je zobrazení přidruženo k příkazu; jinak 0.

## <a name="cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>CMouseManager::GetViewIconId

Načte ikonu přidruženou k ID zobrazení.

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Parametry

*iViewId*<br/>
[v] ID zobrazení.

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku ikony, pokud je úspěšný; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud zobrazení není nejprve registrována pomocí [CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>CMouseManager::GetViewIdByName

Načte ID zobrazení přidružené k názvu zobrazení.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
[v] Název zobrazení.

### <a name="return-value"></a>Návratová hodnota

ID zobrazení v případě úspěchu; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda prohledává zobrazení registrovaná pomocí [CMouseManager::AddView](#addview).

## <a name="cmousemanagergetviewnames"></a><a name="getviewnames"></a>CMouseManager::GetViewNames

Načte seznam všech registrovaných názvů zobrazení.

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*název*<br/>
[out] Odkaz na `CStringList` objekt.

### <a name="remarks"></a>Poznámky

Tato metoda vyplní parametr `listOfNames` názvy všech zobrazení registrovaných pomocí [CMouseManager::AddView](#addview).

## <a name="cmousemanagerloadstate"></a><a name="loadstate"></a>CMouseManager::LoadState

Načte stav [třídy CMouseManager](../../mfc/reference/cmousemanager-class.md) z registru.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Cesta klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Informace o stavu načtené z registru zahrnují registrovaná zobrazení, identifikátory zobrazení a přidružené příkazy. Pokud je parametr *lpszProfileName* null, `CMouseManager` tato funkce načte data z výchozího umístění registru řízeného [třídou CWinAppEx](../../mfc/reference/cwinappex-class.md).

Ve většině případů není třeba volat tuto funkci přímo. Nazývá se jako součást procesu inicializace pracovního prostoru. Další informace o procesu inicializace pracovního prostoru naleznete v tématu [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

## <a name="cmousemanagersavestate"></a><a name="savestate"></a>CMouseManager::Uložitstav

Zapíše stav [třídy CMouseManager](../../mfc/reference/cmousemanager-class.md) do registru.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Cesta klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Informace o stavu zapsané do registru zahrnují všechna registrovaná zobrazení, identifikátory zobrazení a přidružené příkazy. Pokud je parametr *lpszProfileName* null, `CMouseManager` tato funkce zapíše data do výchozího umístění registru řízeného [třídou CWinAppEx](../../mfc/reference/cwinappex-class.md).

Ve většině případů není třeba volat tuto funkci přímo. Nazývá se jako součást procesu serializace pracovního prostoru. Další informace o procesu serializace pracovního prostoru naleznete v tématu [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

## <a name="cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk

Přidruží vlastní příkaz k zobrazení, které je nejprve zaregistrováno u správce myši.

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*iViewId*<br/>
[v] Identifikátor zobrazení.

*uiCmd*<br/>
[v] Identifikátor příkazu.

### <a name="remarks"></a>Poznámky

Chcete-li přidružit vlastní příkaz k zobrazení, musíte nejprve zaregistrovat zobrazení pomocí [CMouseManager::AddView](#addview). Metoda `AddView` vyžaduje identifikátor zobrazení jako vstupní parametr. Po registraci zobrazení můžete `CMouseManager::SetCommandForDblClk` volat se stejným vstupním parametrem `AddView`identifikátoru zobrazení, který jste zadali . Poté, když uživatel poklepe myší v registrovaném zobrazení, aplikace spustí příkaz označený *uiCmd.* Chcete-li podporovat vlastní chování myši, budete také muset přizpůsobit zobrazení registrované u správce myši. Další informace o chování vlastní myši naleznete v [tématu Přizpůsobení klávesnice a myši](../keyboard-and-mouse-customization.md).

Pokud *uiCmd* je nastavena na 0, zadané zobrazení již není přidružen k příkazu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md)
