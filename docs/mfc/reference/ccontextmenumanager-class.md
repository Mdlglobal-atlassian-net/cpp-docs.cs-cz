---
title: Ccontextmenumanager – třída
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
ms.openlocfilehash: 49e9b1cd12bee562daaf4ffb40492c80d8549ec3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639331"
---
# <a name="ccontextmenumanager-class"></a>Ccontextmenumanager – třída

`CContextMenuManager` Objektu spravuje místní nabídky, také známé jako kontextové nabídky.

## <a name="syntax"></a>Syntaxe

```
class CContextMenuManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Vytvoří `CContextMenuManager` objektu.|
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CContextMenuManager::AddMenu](#addmenu)|Přidá novou nabídku.|
|[CContextMenuManager::GetMenuById](#getmenubyid)|Vrátí popisovač do nabídky přidružené k ID zadaného prostředku.|
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Vrátí popisovač do nabídky, která odpovídá názvu zadaná nabídky.|
|[CContextMenuManager::GetMenuNames](#getmenunames)|Vrátí seznam hodnot názvy nabídek.|
|[CContextMenuManager::LoadState](#loadstate)|Načte místní nabídky, které jsou uložené v registru Windows.|
|[CContextMenuManager::ResetState](#resetstate)|Vymaže nabídek z nabídky Správce kontextu.|
|[CContextMenuManager::SaveState](#savestate)|Uloží místní nabídky do registru Windows.|
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Ovládací prvky, zda `CContextMenuManager` při ukazuje novou nabídku ukončí aktivní nabídku.|
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Zobrazí Zadaná místní nabídce.|
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Zobrazí Zadaná místní nabídce. Vrátí index příkaz vybrané nabídky.|

## <a name="remarks"></a>Poznámky

`CContextMenuManager` Spravuje místní nabídky a zajišťuje, že mají konzistentní vzhled.

Nevytvářejte `CContextMenuManager` objekt ručně. Vytvoří rozhraní framework vaší aplikace `CContextMenuManager` objektu. Nicméně byste měli volat [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) při inicializaci vaší aplikace. Po inicializaci správce kontextu, použijte metodu [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) získat ukazatel na místní správce pro vaši aplikaci.

Můžete vytvořit místní nabídky za běhu pomocí volání `AddMenu`. Pokud chcete zobrazit v nabídce bez první přijímání vstupu uživatele, zavolejte `ShowPopupMenu`. `TrackPopupMenu` se používá, pokud chcete vytvořit nabídku a počkat na vstup uživatele. `TrackPopupMenu` Vrátí index vybraného příkazu nebo 0, pokud uživatel ale ukončila se bez provedení výběru.

`CContextMenuManager` Můžete také uložit a načíst jeho stav do registru Windows.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak přidat nabídku `CContextMenuManager` objektu a jak není zavřít aktivní rozbalovací nabídky při `CContextMenuManager` objekt zobrazuje nové místní nabídky. Tento fragment kódu je součástí [ukázková vlastní stránky](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CContextMenuManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcontextmenumanager.h

##  <a name="addmenu"></a>  CContextMenuManager::AddMenu

Přidá novou místní nabídku [ccontextmenumanager –](../../mfc/reference/ccontextmenumanager-class.md).

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
[in] ID prostředku pro řetězec, který obsahuje název nové nabídky.

*uiMenuResId*<br/>
[in] ID nabídky prostředku.

*lpszName*<br/>
[in] Řetězec, který obsahuje název nové nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud metoda byla úspěšná. 0, jestliže metoda selže.

### <a name="remarks"></a>Poznámky

Tato metoda selže, pokud *uiMenuResId* je neplatný nebo pokud jiné nabídky se stejným názvem již probíhá `CContextMenuManager`.

##  <a name="ccontextmenumanager"></a>  CContextMenuManager::CContextMenuManager

Vytvoří [ccontextmenumanager –](../../mfc/reference/ccontextmenumanager-class.md) objektu.

```
CContextMenuManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů by neměl vytvářet `CContextMenuManager` ručně. Vytvoří rozhraní framework vaší aplikace `CContextMenuManager` objektu. Měli byste zavolat [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) během inicializace vaší aplikace. Chcete-li ukazatel vrátit do správce kontextu, zavolejte [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).

##  <a name="getmenubyid"></a>  CContextMenuManager::GetMenuById

Vrátí popisovač do nabídky přidružené k ID daného prostředku.

```
HMENU GetMenuById(UINT nMenuResId) const;
```

### <a name="parameters"></a>Parametry

*nMenuResId*<br/>
[in] ID prostředku pro nabídku.

### <a name="return-value"></a>Návratová hodnota

Popisovač pro příslušné nabídky nebo `NULL` Pokud nebyl nalezen v nabídce.

##  <a name="getmenubyname"></a>  CContextMenuManager::GetMenuByName

Vrátí popisovač do konkrétní nabídky.

```
HMENU GetMenuByName(
    LPCTSTR lpszName,
    UINT* puiOrigResID = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
[in] Řetězec, který obsahuje název nabídky k načtení.

*puiOrigResID*<br/>
[out] Ukazatel UINT. Tento parametr obsahuje ID prostředku zadaného nabídky, pokud nalezen.

### <a name="return-value"></a>Návratová hodnota

V nabídce, která odpovídá názvu, který byl zadán popisovač *lpszName*. Hodnota NULL, pokud neexistuje žádné nabídky s názvem *lpszName*.

### <a name="remarks"></a>Poznámky

Pokud tato metoda vyhledá nabídka, která odpovídá *lpszName*, `GetMenuByName` ukládá ID prostředku nabídky v parametru *puiOrigResID*.

##  <a name="getmenunames"></a>  CContextMenuManager::GetMenuNames

Vrátí seznam názvů nabídek, které jsou přidány do [ccontextmenumanager –](../../mfc/reference/ccontextmenumanager-class.md).

```
void GetMenuNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*listOfNames*<br/>
[out] Odkaz na [CStringList](../../mfc/reference/cstringlist-class.md) parametru. Tato metoda zapíše seznam názvů nabídek, které tomuto parametru.

##  <a name="loadstate"></a>  CContextMenuManager::LoadState

Načte informace o přidružené [ccontextmenumanager – třída](../../mfc/reference/ccontextmenumanager-class.md) z registru Windows.

```
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Řetězec, který obsahuje relativní cestu klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

*LpszProfileName* parametr není absolutní cestu pro položky registru. Je relativní cestu, která se přidá na konec výchozí klíč registru pro vaši aplikaci. Chcete-li získat nebo nastavit klíč registru výchozí, použijte metody [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) v uvedeném pořadí.

Pomocí této metody [CContextMenuManager::SaveState](#savestate) uložit místní nabídky do registru.

##  <a name="resetstate"></a>  CContextMenuManager::ResetState

Vymaže všechny položky z místní nabídky přidružené [ccontextmenumanager – třída](../../mfc/reference/ccontextmenumanager-class.md).

```
virtual BOOL ResetState();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je metoda úspěšná. FALSE, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tato metoda vymaže rozbalovací nabídky a odebere je ze `CContextMenuManager`.

##  <a name="savestate"></a>  CContextMenuManager::SaveState

Uloží informace o přidružené [ccontextmenumanager – třída](../../mfc/reference/ccontextmenumanager-class.md) do registru Windows.

```
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Řetězec, který obsahuje relativní cestu klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je metoda úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

*LpszProfileName* parametr není absolutní cestu pro položky registru. Je relativní cestu, která se přidá na konec výchozí klíč registru pro vaši aplikaci. Chcete-li získat nebo nastavit klíč registru výchozí, použijte metody [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) v uvedeném pořadí.

Pomocí této metody [CContextMenuManager::LoadState](#loadstate) načíst místní nabídky z registru.

##  <a name="setdontcloseactivemenu"></a>  CContextMenuManager::SetDontCloseActiveMenu

Ovládací prvky, zda [ccontextmenumanager –](../../mfc/reference/ccontextmenumanager-class.md) zavře aktivní v rozbalovací nabídce poznat novou místní nabídky.

```
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
[in] Parametr logické hodnoty, která určuje, zda se zavřít aktivní rozbalovací nabídky. Hodnota TRUE označuje, že není uzavřená v rozbalovací nabídce aktivní. Hodnota FALSE označuje, že je uzavřena v rozbalovací nabídce aktivní.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CContextMenuManager` zavře aktivní rozbalovací nabídky.

##  <a name="showpopupmenu"></a>  CContextMenuManager::ShowPopupMenu

Zobrazí Zadaná místní nabídce.

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
[in] ID prostředku v nabídce, která se zobrazí takto.

*x*<br/>
[in] Vodorovný posun nabídku souřadnice klienta.

*y*<br/>
[in] Svislý posun pro nabídku souřadnice klienta

*pWndOwner*<br/>
[in] Ukazatel na nadřazené okno místní nabídky.

*bOwnMessage*<br/>
[in] Parametr logické hodnoty, která určuje, jak se směrují zprávy. Pokud *bOwnMessage* je FALSE, standardní knihovny MFC směrování se používá. V opačném případě *pWndOwner* přijme zprávy.

*hmenuPopup*<br/>
[in] Popisovač nabídky, která se zobrazí takto.

*bAutoDestroy*<br/>
[in] Parametr logické hodnoty označující, zda v nabídce se automaticky odstraní.

*bRightAlign*<br/>
[in] Parametr logické hodnoty, která určuje, jak jsou zarovnány položky nabídky. Pokud *bRightAlign* má hodnotu TRUE, v nabídce zarovnán doprava pro pořadí čtení zprava doleva.

### <a name="return-value"></a>Návratová hodnota

První přetížení metody vrátí nenulovou hodnotu, pokud metoda zobrazí v nabídce úspěšně; jinak 0. Druhé přetížení metody vrací ukazatel na [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) Pokud v místní nabídce se zobrazí správně; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tento způsob se podobá metodě [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) v tom, že obě metody zobrazit místní nabídku. Ale `TrackPopupMenu` vrátí index příkaz vybrané nabídky.

Pokud parametr *bAutoDestroy* má hodnotu FALSE, je nutné volat ručně zděděnou `DestroyMenu` metodu pro uvolnění paměťových prostředků. Výchozí implementace `ShowPopupMenu` nepoužívá parametr *bAutoDestroy*. Je k dispozici pro budoucí použití nebo pro vlastní třídy odvozené od `CContextMenuManager` třídy.

##  <a name="trackpopupmenu"></a>  CContextMenuManager::TrackPopupMenu

Zadaná místní nabídce se zobrazí a vrátí index příkazu vybrané místní nabídky.

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
[in] Popisovač nabídku, která zobrazuje tuto metodu.

*x*<br/>
[in] Vodorovný posun nabídku souřadnice klienta.

*y*<br/>
[in] Svislý posun pro nabídku souřadnice klienta.

*pWndOwner*<br/>
[in] Ukazatel na nadřazené okno místní nabídky.

*bRightAlign*<br/>
[in] Parametr logické hodnoty, která určuje, jak jsou zarovnány položky nabídky. Pokud *bRightAlign* má hodnotu TRUE, v nabídce zarovnán doprava pro pořadí čtení zprava doleva. Pokud *bRightAlign* má hodnotu FALSE, v nabídce zarovnané vlevo pořadí čtení zleva doprava.

### <a name="return-value"></a>Návratová hodnota

ID nabídky příkazu příkazu, který uživatel vybere; 0, pokud uživatel nezavře nabídku bez výběru příkazu nabídky.

### <a name="remarks"></a>Poznámky

Tato metoda funguje jako modální volání zobrazit místní nabídku. Aplikace nebude pokračovat na následující řádek kódu, dokud uživatel zavře nabídku nebo vybere příkaz. Je alternativní metoda, která slouží k zobrazení místní nabídky [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Tato metoda není modální volání a nevrátí ID vybraného příkazu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
