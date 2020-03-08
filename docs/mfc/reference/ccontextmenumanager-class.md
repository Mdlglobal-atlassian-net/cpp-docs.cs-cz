---
title: CContextMenuManager – třída
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
ms.openlocfilehash: c8a51a33c69b09d0ecd61520b5f1c9ff18c290a0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78868987"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager – třída

Objekt `CContextMenuManager` spravuje místní nabídky, označované také jako kontextové nabídky.

## <a name="syntax"></a>Syntaxe

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Vytvoří objekt `CContextMenuManager`.|
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CContextMenuManager:: PřidatNabídku](#addmenu)|Přidá novou místní nabídku.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Vrátí popisovač do nabídky přidružené k zadanému ID prostředku.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Vrátí popisovač nabídky, který odpovídá zadanému názvu nabídky.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Vrátí seznam názvů nabídek.|
|[CContextMenuManager:: LoadState](#loadstate)|Načte místní nabídky uložené v registru Windows.|
|[CContextMenuManager:: funkce ResetState](#resetstate)|Vymaže místní nabídky ze správce místní nabídky.|
|[CContextMenuManager:: SaveState](#savestate)|Uloží místní nabídky do registru systému Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Určuje, zda `CContextMenuManager` zavře aktivní místní nabídku, když se zobrazí nová místní nabídka.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Zobrazí určenou místní nabídku.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Zobrazí určenou místní nabídku. Vrátí index vybraného příkazu nabídky.|

## <a name="remarks"></a>Poznámky

`CContextMenuManager` spravuje místní nabídky a zajišťuje konzistentní vzhled.

Objekt `CContextMenuManager` byste neměli vytvářet ručně. Rozhraní aplikace vytvoří objekt `CContextMenuManager`. Nicméně při inicializaci aplikace byste měli zavolat metodu [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) . Po inicializaci správce kontextu použijte metodu [CWinAppEx:: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) a získejte ukazatel na správce kontextu vaší aplikace.

Můžete vytvořit místní nabídky za běhu voláním `AddMenu`. Chcete-li zobrazit nabídku bez prvotního vstupu uživatele, zavolejte `ShowPopupMenu`. `TrackPopupMenu` se používá v případě, že chcete vytvořit nabídku a počkat na vstup uživatele. `TrackPopupMenu` vrátí index vybraného příkazu nebo 0, pokud byl uživatel ukončen bez výběru všeho.

`CContextMenuManager` také může uložit a načíst svůj stav do registru systému Windows.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat nabídku do objektu `CContextMenuManager` a jak nezavřít aktivní místní nabídku, když se v objektu `CContextMenuManager` zobrazí nová místní nabídka. Tento fragment kódu je součástí [ukázky vlastních stránek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcontextmenumanager. h

##  <a name="addmenu"></a>CContextMenuManager:: PřidatNabídku

Přidá novou místní nabídku do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
BOOL AddMenu(
    UINT uiMenuNameResId,
    UINT uiMenuResId);

BOOL AddMenu(
    LPCTSTR lpszName,
    UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*uiMenuNameResId*<br/>
pro ID prostředku pro řetězec, který obsahuje název nové nabídky.

*uiMenuResId*<br/>
pro ID prostředku nabídky

*lpszName*<br/>
pro Řetězec, který obsahuje název nové nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla metoda úspěšná; 0, pokud se metoda nezdařila.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdařila, pokud je *uiMenuResId* neplatný nebo pokud už je v `CContextMenuManager`jiná nabídka se stejným názvem.

##  <a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager

Vytvoří objekt [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) .

```
CContextMenuManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů byste neměli `CContextMenuManager` vytvořit ručně. Rozhraní aplikace vytvoří objekt `CContextMenuManager`. Během inicializace aplikace byste měli zavolat metodu [CWinAppEx:: InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) . Chcete-li získat ukazatel na správce kontextu, zavolejte [CWinAppEx:: GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

##  <a name="getmenubyid"></a>CContextMenuManager::GetMenuById

Vrátí popisovač do nabídky přidružené k danému ID prostředku.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parametry

*nMenuResId*<br/>
pro ID prostředku pro nabídku

### <a name="return-value"></a>Návratová hodnota

Popisovač přidružené nabídky nebo `NULL`, pokud se nabídka nenajde.

##  <a name="getmenubyname"></a>CContextMenuManager::GetMenuByName

Vrátí popisovač do konkrétní nabídky.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
pro Řetězec, který obsahuje název nabídky, která se má načíst.

*puiOrigResID*<br/>
mimo Ukazatel na objekt UINT. Tento parametr obsahuje ID prostředku zadané nabídky, pokud je nalezen.

### <a name="return-value"></a>Návratová hodnota

Popisovač nabídky, který odpovídá názvu určenému parametrem *lpszName*. Hodnota NULL, pokud není k dispozici žádná nabídka s názvem *lpszName*.

### <a name="remarks"></a>Poznámky

Pokud tato metoda najde nabídku, která odpovídá *lpszName*, `GetMenuByName` ukládá ID prostředku nabídky do parametru *puiOrigResID*.

##  <a name="getmenunames"></a>CContextMenuManager::GetMenuNames

Vrátí seznam názvů nabídek přidaných do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*listOfNames*<br/>
mimo Odkaz na parametr [CStringList](../../mfc/reference/cstringlist-class.md) . Tato metoda zapíše seznam názvů nabídek do tohoto parametru.

##  <a name="loadstate"></a>CContextMenuManager:: LoadState

Načte informace spojené s [třídou CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) z registru systému Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Řetězec, který obsahuje relativní cestu ke klíči registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Parametr *lpszProfileName* není absolutní cesta pro položku registru. Jedná se o relativní cestu, která se přidá na konec výchozího klíče registru pro vaši aplikaci. Chcete-li získat nebo nastavit výchozí klíč registru, použijte metody [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) v uvedeném pořadí.

Pomocí metody [CContextMenuManager:: SaveState](#savestate) uložte místní nabídky do registru.

##  <a name="resetstate"></a>CContextMenuManager:: funkce ResetState

Vymaže všechny položky z místních nabídek přidružených ke [třídě CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; FALSE, pokud dojde k selhání.

### <a name="remarks"></a>Poznámky

Tato metoda vymaže místní nabídky a odebere je z `CContextMenuManager`.

##  <a name="savestate"></a>CContextMenuManager:: SaveState

Uloží informace přidružené ke [třídě CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) do registru systému Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
pro Řetězec, který obsahuje relativní cestu ke klíči registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Parametr *lpszProfileName* není absolutní cesta pro položku registru. Jedná se o relativní cestu, která se přidá na konec výchozího klíče registru pro vaši aplikaci. Chcete-li získat nebo nastavit výchozí klíč registru, použijte metody [CWinAppEx:: GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx:: SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) v uvedeném pořadí.

K načtení místních nabídek z registru použijte metodu [CContextMenuManager:: LoadState](#loadstate) .

##  <a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu

Určuje, zda [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) zavře aktivní místní nabídku při zobrazení nové místní nabídky.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
pro Logický parametr, který určuje, zda má být zavřena aktivní místní nabídka. Hodnota TRUE značí, že aktivní místní nabídka není zavřena. Hodnota FALSE označuje, že aktivní místní nabídka je zavřena.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CContextMenuManager` zavře aktivní místní nabídku.

##  <a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu

Zobrazí určenou místní nabídku.

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
pro ID prostředku nabídky, kterou bude tato metoda zobrazovat.

*znak*<br/>
pro Vodorovný posun místní nabídky v souřadnicích klienta.

*požadované*<br/>
pro Svislý posun místní nabídky v souřadnicích klienta

*pWndOwner*<br/>
pro Ukazatel na nadřazené okno místní nabídky.

*bOwnMessage*<br/>
pro Logický parametr, který určuje, jak jsou zprávy směrovány. Pokud je *BOWNMESSAGE* false, použije se standardní směrování MFC. V opačném případě *pWndOwner* obdrží zprávy.

*hmenuPopup*<br/>
pro Popisovač nabídky, kterou tato metoda zobrazí

*bAutoDestroy*<br/>
pro Logický parametr, který označuje, zda bude nabídka automaticky zničena.

*bRightAlign*<br/>
pro Logický parametr, který určuje, jak jsou zarovnány položky nabídky. Pokud má *bRightAlign* hodnotu true, je nabídka zarovnána vpravo ke směru čtení zprava doleva.

### <a name="return-value"></a>Návratová hodnota

První přetížení metody vrátí nenulovou hodnotu, pokud metoda zobrazí nabídku úspěšně. v opačném případě 0. Druhá metoda Overload vrátí ukazatel na [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) , pokud se místní nabídka zobrazuje správně. jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda se podobá metodě [CContextMenuManager:: TrackPopupMenu](#trackpopupmenu) v tom, že obě metody zobrazují místní nabídku. `TrackPopupMenu` však vrátí index vybraného příkazu nabídky.

Pokud je parametr *BAUTODESTROY* false, je nutné ručně volat zděděnou `DestroyMenu` metodu pro uvolnění paměťových prostředků. Výchozí implementace `ShowPopupMenu` nepoužívá parametr *bAutoDestroy*. Je k dispozici pro budoucí použití nebo pro vlastní třídy odvozené od třídy `CContextMenuManager`.

##  <a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu

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
pro Popisovač místní nabídky, kterou tato metoda zobrazuje

*znak*<br/>
pro Vodorovný posun místní nabídky v souřadnicích klienta.

*požadované*<br/>
pro Svislý posun místní nabídky v souřadnicích klienta.

*pWndOwner*<br/>
pro Ukazatel na nadřazené okno místní nabídky.

*bRightAlign*<br/>
pro Logický parametr, který určuje, jak jsou zarovnány položky nabídky. Pokud má *bRightAlign* hodnotu true, je nabídka zarovnána vpravo ke směru čtení zprava doleva. Pokud je *BRIGHTALIGN* false, nabídka je zarovnána vlevo pro pořadí čtení zleva doprava.

### <a name="return-value"></a>Návratová hodnota

ID příkazu nabídky, který uživatel zvolí; 0, pokud uživatel zavře místní nabídku bez výběru příkazu nabídky.

### <a name="remarks"></a>Poznámky

Tato metoda funguje jako modální volání pro zobrazení místní nabídky. V kódu aplikace nebude pokračovat následující řádek, dokud uživatel buď nezavře místní nabídku, nebo nevybere příkaz. Alternativná metoda, kterou lze použít k zobrazení místní nabídky, je [CContextMenuManager:: ShowPopupMenu](#showpopupmenu). Tato metoda není modálním voláním a nebude vracet ID vybraného příkazu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
