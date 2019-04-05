---
title: CMouseManager Class
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
ms.openlocfilehash: f92a72e36fecbb39e57cbdf9583047aca0c1ebd5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773733"
---
# <a name="cmousemanager-class"></a>CMouseManager Class

Umožňuje uživateli přidružit různé příkazy ke konkrétním [CView](../../mfc/reference/cview-class.md) objektu při poklepání uvnitř daného zobrazení.

## <a name="syntax"></a>Syntaxe

```
class CMouseManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMouseManager::AddView](#addview)|Přidá `CView` objektu **přizpůsobení** dialogové okno. **Přizpůsobení** dialogové okno umožňuje uživateli přidružit dvakrát klikněte na příkaz pro každou z uvedených zobrazení.|
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Vrátí příkaz, který se spouští při poklepání uvnitř zadaná zobrazení.|
|[CMouseManager::GetViewIconId](#getviewiconid)|Vrátí ikony přidružené k ID zadané zobrazení.|
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Vrátí ID zobrazení související s názvem zadaného zobrazení.|
|[CMouseManager::GetViewNames](#getviewnames)|Načte seznam všech názvů přidané zobrazení.|
|[CMouseManager::LoadState](#loadstate)|Načtení `CMouseManager` stavu z registru Windows.|
|[CMouseManager::SaveState](#savestate)|Zapíše `CMouseManager` stav do registru Windows.|
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Přidruží zadaný příkaz a zadané zobrazení.|

## <a name="remarks"></a>Poznámky

`CMouseManager` Třídy udržuje kolekci `CView` objekty. Každé zobrazení je identifikován název a identifikátor. Tato zobrazení jsou uvedeny v **přizpůsobení** dialogové okno. Uživatel může změnit příkaz, který je přidružený k libovolné zobrazení prostřednictvím **přizpůsobení** dialogové okno. Přidružený příkaz je proveden, když uživatel poklepe v tomto zobrazení. Z hlediska kódování z toho důvodu musí zpracovat zprávu WM_LBUTTONDBLCLK a volání [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkce v kódu, který `CView` objektu...

Nevytvářejte `CMouseManager` objekt ručně. Vytvoří se v rámci rozhraní vaší aplikace. Je také zničí automaticky při ukončení aplikace uživatelem. Chcete-li získat ukazatel myši správci pro vaši aplikaci, zavolejte [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CMouseManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmousemanager.h

##  <a name="addview"></a>  CMouseManager::AddView

Zaregistruje [CView](../../mfc/reference/cview-class.md) objektu [cmousemanager – třída](../../mfc/reference/cmousemanager-class.md) pro podporu myši vlastní chování.

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
[in] ID zobrazení

*uiViewNameResId*<br/>
[in] ID prostředku řetězce, který odkazuje na název zobrazení.

*uiIconId*<br/>
[in] ID ikony zobrazení

*iId*<br/>
[in] ID zobrazení

*lpszViewName*<br/>
[in] Název zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Za účelem podpory chování vlastní myši, zobrazení, musí zaregistrovat `CMouseManager` objektu. Libovolný objekt odvozený od `CView` třídy lze registrovat pomocí myši správce. Řetězec a ikonu přiřazenou k zobrazení se zobrazují v **myši** karty **vlastní** dialogové okno.

Zodpovídá programátor k vytváření a údržbě zobrazení ID, jako *iViewId* a *iId*.

Další informace o tom, jak poskytnout vlastní myši chování najdete v tématu [přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak se načítají ukazatel na `CMouseManager` s použitím `CWinAppEx::GetMouseManager` metoda a `AddView` metoda ve `CMouseManager` třídy. Tento fragment kódu je součástí [vzorek sběru stavu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]

##  <a name="getviewdblclickcommand"></a>  CMouseManager::GetViewDblClickCommand

Vrátí příkaz, který se spouští při poklepání uvnitř zadaná zobrazení.

```
UINT GetViewDblClickCommand(int iId) const;
```

### <a name="parameters"></a>Parametry

*iId*<br/>
[in] ID zobrazení.

### <a name="return-value"></a>Návratová hodnota

Identifikátor příkazu, pokud zobrazení je spojen s příkazem; jinak 0.

##  <a name="getviewiconid"></a>  CMouseManager::GetViewIconId

Načte ikonu přiřazenou k ID zobrazení

```
UINT GetViewIconId(int iViewId) const;
```

### <a name="parameters"></a>Parametry

*iViewId*<br/>
[in] ID zobrazení.

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku ikony v případě úspěchu; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud zobrazení není nejprve registrována pomocí [CMouseManager::AddView](#addview).

##  <a name="getviewidbyname"></a>  CMouseManager::GetViewIdByName

Načte zobrazení ID přidružené k názvu zobrazení.

```
int GetViewIdByName(LPCTSTR lpszName) const;
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
[in] Název zobrazení.

### <a name="return-value"></a>Návratová hodnota

ID zobrazení v případě úspěchu; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda vyhledává registrovaných pomocí zobrazení [CMouseManager::AddView](#addview).

##  <a name="getviewnames"></a>  CMouseManager::GetViewNames

Načte seznam všech názvů registrovaných zobrazení.

```
void GetViewNames(CStringList& listOfNames) const;
```

### <a name="parameters"></a>Parametry

*listOfNames*<br/>
[out] Odkaz na `CStringList` objektu.

### <a name="remarks"></a>Poznámky

Tato metoda vyplní parametr `listOfNames` s názvy všech registrovaných pomocí zobrazení [CMouseManager::AddView](#addview).

##  <a name="loadstate"></a>  CMouseManager::LoadState

Načte stav [cmousemanager – třída](../../mfc/reference/cmousemanager-class.md) z registru.

```
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Cesta klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Informace o stavu načíst z registru obsahuje registrovaná zobrazení, zobrazit identifikátory a přidružené příkazy. Pokud parametr *lpszProfileName* má hodnotu NULL, tato funkce načítá `CMouseManager` data z výchozího umístění registru řídí [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md).

Ve většině případů není nutné tuto funkci volat přímo. Volá se jako součást procesu inicializace pracovního prostoru. Další informace o procesu inicializace pracovního prostoru najdete v tématu [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).

##  <a name="savestate"></a>  CMouseManager::SaveState

Zapíše stav [cmousemanager – třída](../../mfc/reference/cmousemanager-class.md) do registru.

```
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Cesta klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Informace o stavu zapsána do registru obsahuje přidružené příkazy, zobrazit identifikátory a všech registrovaných zobrazení. Pokud parametr *lpszProfileName* má hodnotu NULL, tato funkce zapíše `CMouseManager` data do výchozího umístění registru řídí [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md).

Ve většině případů není nutné tuto funkci volat přímo. Volá se jako součást procesu serializace pracovního prostoru. Další informace o pracovním prostoru procesu serializace naleznete v tématu [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).

##  <a name="setcommandfordblclk"></a>  CMouseManager::SetCommandForDblClk

Zobrazení, které je nejprve registrována pomocí myši správce přiřadí vlastní příkaz.

```
void SetCommandForDblClk(
    int iViewId,
    UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*iViewId*<br/>
[in] Identifikátor zobrazení.

*uiCmd*<br/>
[in] Identifikátor příkazu.

### <a name="remarks"></a>Poznámky

Aby bylo možné přidružit k zobrazení vlastního příkazu, musíte se nejprve zaregistrovat zobrazení pomocí [CMouseManager::AddView](#addview). `AddView` Metoda vyžaduje zobrazení identifikátor jako vstupní parametr. Jakmile si zaregistrujete zobrazení, můžete volat `CMouseManager::SetCommandForDblClk` pomocí stejného zobrazení identifikátor vstupní parametr, který jste zadali do `AddView`. Po tomto datu, když uživatel pokliká myší v registrovaných zobrazení, aplikace se provést příkaz indikován *uiCmd.* Pro podporu myši vlastní chování, bude také muset přizpůsobit zobrazení zaregistrované pomocí myši správce. Další informace týkající se myši vlastní chování najdete v tématu [přizpůsobení klávesnice a myši](../keyboard-and-mouse-customization.md).

Pokud *uiCmd* je nastavena na hodnotu 0, zadané zobrazení je už přidružený příkaz.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)<br/>
[Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md)
