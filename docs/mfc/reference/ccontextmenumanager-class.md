---
title: Třída CContextMenuManager
ms.date: 11/04/2016
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
ms.openlocfilehash: c676355ebf44d6cc02bfa66ac870757627ae5a58
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754802"
---
# <a name="ccontextmenumanager-class"></a>Třída CContextMenuManager

Objekt `CContextMenuManager` spravuje místní nabídky, známé také jako kontextové nabídky.

## <a name="syntax"></a>Syntaxe

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Vytvoří `CContextMenuManager` objekt.|
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CContextMenuManager::AddMenu](#addmenu)|Přidá novou místní nabídku.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Vrátí popisovač do nabídky přidružené k ID poskytnutého prostředku.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Vrátí popisovač do nabídky, která odpovídá zadaný název nabídky.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Vrátí seznam názvů nabídek.|
|[CContextMenuManager::LoadState](#loadstate)|Načte místní nabídky uložené v registru systému Windows.|
|[CContextMenuManager::ResetState](#resetstate)|Vymaže místní nabídky ze správce místní nabídky.|
|[CContextMenuManager::SaveState](#savestate)|Uloží místní nabídky do registru systému Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Určuje, `CContextMenuManager` zda zavře aktivní místní nabídku, když se zobrazí nová místní nabídka.|
|[CContextMenuManager::Nabídka ShowPopup](#showpopupmenu)|Zobrazí zadanou místní nabídku.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Zobrazí zadanou místní nabídku. Vrátí index vybraného příkazu nabídky.|

## <a name="remarks"></a>Poznámky

`CContextMenuManager`spravuje místní nabídky a zajišťuje, že mají konzistentní vzhled.

Objekt byste neměli vytvářet `CContextMenuManager` ručně. V rámci aplikace vytvoří `CContextMenuManager` objekt. Však byste měli volat [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) při inicializování aplikace. Po inicializaci správce kontextu použijte metodu [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) k získání ukazatele na správce kontextu pro vaši aplikaci.

Místní nabídky můžete vytvořit za běhu `AddMenu`voláním . Chcete-li zobrazit nabídku bez předchozího `ShowPopupMenu`příjmu vstupu uživatele, zavolejte . `TrackPopupMenu`se používá, když chcete vytvořit nabídku a čekat na vstup uživatele. `TrackPopupMenu`vrátí index vybraného příkazu nebo 0, pokud uživatel ukončit bez výběru nic.

Můžete `CContextMenuManager` také uložit a načíst jeho stav do registru systému Windows.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat nabídku k objektu `CContextMenuManager` a jak nezavřít aktivní `CContextMenuManager` rozbalovací nabídku, když objekt zobrazí novou rozbalovací nabídku. Tento fragment kódu je součástí [ukázky vlastních stránek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcontextmenumanager.h

## <a name="ccontextmenumanageraddmenu"></a><a name="addmenu"></a>CContextMenuManager::AddMenu

Přidá novou místní nabídku do [aplikace CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*uiMenuNameResd*<br/>
[v] ID prostředku pro řetězec, který obsahuje název nové nabídky.

*uiMenuResId*<br/>
[v] ID prostředku nabídky.

*název lpsz*<br/>
[v] Řetězec, který obsahuje název nové nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla metoda úspěšná; 0, pokud se metoda nezdaří.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud *uiMenuResId* je neplatný `CContextMenuManager`nebo pokud jiné nabídky se stejným názvem již je v .

## <a name="ccontextmenumanagerccontextmenumanager"></a><a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Vytvoří [cContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objektu.

```
CContextMenuManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů byste neměli `CContextMenuManager` vytvářet ručně. V rámci aplikace vytvoří `CContextMenuManager` objekt. Měli byste volat [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) během inicializace aplikace. Chcete-li získat ukazatel na správce kontextu, zavolejte [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

## <a name="ccontextmenumanagergetmenubyid"></a><a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Vrátí popisovač do nabídky přidružené k danému ID prostředku.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parametry

*nMenuResId*<br/>
[v] ID prostředku pro nabídku.

### <a name="return-value"></a>Návratová hodnota

Popisovač přidružené nabídky `NULL` nebo pokud nabídka nebyla nalezena.

## <a name="ccontextmenumanagergetmenubyname"></a><a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Vrátí popisovač do určité nabídky.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
[v] Řetězec, který obsahuje název nabídky načíst.

*puiOrigResID*<br/>
[out] Ukazatel na UINT. Tento parametr obsahuje ID prostředku zadané nabídky, pokud je nalezen.

### <a name="return-value"></a>Návratová hodnota

Popisovač nabídky, která odpovídá názvu, který byl zadán *lpszName*. NULL, pokud neexistuje žádná nabídka s názvem *lpszName*.

### <a name="remarks"></a>Poznámky

Pokud tato metoda najde nabídku, která `GetMenuByName` odpovídá *lpszName*, uloží ID prostředku nabídky v parametru *puiOrigResID*.

## <a name="ccontextmenumanagergetmenunames"></a><a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Vrátí seznam názvů nabídek přidaných do [aplikace CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```cpp
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*název*<br/>
[out] Odkaz na [cstringlist](../../mfc/reference/cstringlist-class.md) parametr. Tato metoda zapíše seznam názvů nabídek do tohoto parametru.

## <a name="ccontextmenumanagerloadstate"></a><a name="loadstate"></a>CContextMenuManager::LoadState

Načte informace přidružené ke [třídě CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) z registru systému Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Řetězec, který obsahuje relativní cestu klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Parametr *lpszProfileName* není absolutní cestou pro položku registru. Jedná se o relativní cestu, která je přidána na konec výchozího klíče registru pro vaši aplikaci. Chcete-li získat nebo nastavit výchozí klíč registru, použijte metody [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx::SetRegistryBase.](../../mfc/reference/cwinappex-class.md#setregistrybase)

Pomocí metody [CContextMenuManager::SaveState](#savestate) uložte místní nabídky do registru.

## <a name="ccontextmenumanagerresetstate"></a><a name="resetstate"></a>CContextMenuManager::ResetState

Vymaže všechny položky z místních nabídek přidružených ke [třídě CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; False, pokud dojde k selhání.

### <a name="remarks"></a>Poznámky

Tato metoda vymaže rozbalovací nabídky a `CContextMenuManager`odebere je z .

## <a name="ccontextmenumanagersavestate"></a><a name="savestate"></a>CContextMenuManager::SaveState

Uloží informace přidružené ke [třídě CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) do registru systému Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Řetězec, který obsahuje relativní cestu klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je metoda úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Parametr *lpszProfileName* není absolutní cestou pro položku registru. Jedná se o relativní cestu, která je přidána na konec výchozího klíče registru pro vaši aplikaci. Chcete-li získat nebo nastavit výchozí klíč registru, použijte metody [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx::SetRegistryBase.](../../mfc/reference/cwinappex-class.md#setregistrybase)

Pomocí metody [CContextMenuManager::LoadState](#loadstate) načtěte místní nabídky z registru.

## <a name="ccontextmenumanagersetdontcloseactivemenu"></a><a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Určuje, zda [cContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) zavře aktivní rozbalovací nabídku, když se zobrazí nová rozbalovací nabídka.

```cpp
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
[v] Logický parametr, který určuje, zda má být aktivní rozbalovací nabídka ukončena. Hodnota TRUE označuje, že aktivní rozbalovací nabídka není uzavřena. NEPRAVDA označuje, že aktivní rozbalovací nabídka je zavřená.

### <a name="remarks"></a>Poznámky

Ve výchozím `CContextMenuManager` nastavení zavře aktivní rozbalovací nabídku.

## <a name="ccontextmenumanagershowpopupmenu"></a><a name="showpopupmenu"></a>CContextMenuManager::Nabídka ShowPopup

Zobrazí zadanou místní nabídku.

```
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bRightAlign = FALSE);

virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bOwnMessage = FALSE,
    BOOL bAutoDestroy = TRUE,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parametry

*uiMenuResId*<br/>
[v] ID prostředku nabídky, která se zobrazí v této metodě.

*X*<br/>
[v] Vodorovné odsazení místní nabídky v souřadnicích klienta.

*Y*<br/>
[v] Svislé odsazení místní nabídky v klientských souřadnicích

*pWndVlastník*<br/>
[v] Ukazatel na nadřazené okno místní nabídky.

*bOwnMessage*<br/>
[v] Logický parametr, který označuje způsob směrování zpráv. Pokud *je bOwnMessage* FALSE, použije se standardní směrování knihovny MFC. V opačném případě *pWndOwner* obdrží zprávy.

*hmenuPopup*<br/>
[v] Popisovač nabídky, která se zobrazí v této metodě.

*bAutoDestroy*<br/>
[v] Logický parametr, který označuje, zda bude nabídka automaticky zničena.

*bZarovnat*<br/>
[v] Logický parametr, který označuje, jak jsou položky nabídky zarovnány. Pokud *je bRightAlign* TRUE, nabídka je zarovnána doprava pro pořadí čtení zprava doleva.

### <a name="return-value"></a>Návratová hodnota

První metoda přetížení vrátí nenulovou, pokud metoda zobrazí menu úspěšně; jinak 0. Druhá metoda přetížení vrátí ukazatel [CMFCPopupMenu,](../../mfc/reference/cmfcpopupmenu-class.md) pokud místní nabídka zobrazí správně; jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda se podobá metodě [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) v tom, že obě metody zobrazují místní nabídku. Vrátí `TrackPopupMenu` však index vybraného příkazu nabídky.

Pokud je parametr *bAutoDestroy* FALSE, je nutné `DestroyMenu` ručně volat zděděnou metodu k uvolnění paměťových prostředků. Výchozí implementace `ShowPopupMenu` nepoužívá parametr *bAutoDestroy*. Je k dispozici pro budoucí použití nebo pro `CContextMenuManager` vlastní třídy odvozené z třídy .

## <a name="ccontextmenumanagertrackpopupmenu"></a><a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu

Zobrazí zadanou místní nabídku a vrátí index vybraného příkazu místní nabídky.

```
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,
    int x,
    int y,
    CWnd* pWndOwner,
    BOOL bRightAlign = FALSE);
```

### <a name="parameters"></a>Parametry

*hmenuPopup*<br/>
[v] Popisovač místní nabídky, která se zobrazí v této metodě.

*X*<br/>
[v] Vodorovné odsazení místní nabídky v souřadnicích klienta.

*Y*<br/>
[v] Svislé odsazení pro místní nabídku v souřadnicích klienta.

*pWndVlastník*<br/>
[v] Ukazatel na nadřazené okno místní nabídky.

*bZarovnat*<br/>
[v] Logický parametr, který označuje, jak jsou položky nabídky zarovnány. Pokud *je bRightAlign* TRUE, nabídka je zarovnána doprava pro pořadí čtení zprava doleva. Pokud *je bRightAlign* FALSE, nabídka je zarovnána zleva doprava pro pořadí čtení zleva doprava.

### <a name="return-value"></a>Návratová hodnota

ID příkazu nabídky příkazu, který uživatel zvolí; 0, pokud uživatel zavře místní nabídku bez výběru příkazu nabídky.

### <a name="remarks"></a>Poznámky

Tato metoda funguje jako modální volání pro zobrazení místní nabídky. Aplikace nebude pokračovat na následující řádek v kódu, dokud uživatel buď zavře místní nabídku nebo vybere příkaz. Alternativní metodou, kterou lze použít k zobrazení místní nabídky, je [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Tato metoda není modální volání a nevrátí ID vybraného příkazu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)
