---
title: Cusertoolsmanager – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
dev_langs:
- C++
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2da34eacb7524168f16d05248eee97422a1fb770
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380757"
---
# <a name="cusertoolsmanager-class"></a>Cusertoolsmanager – třída

Udržuje kolekci [cusertool – třída](../../mfc/reference/cusertool-class.md) objekty v aplikaci. Uživatelský nástroj je položka nabídky, která spustí externí aplikaci. `CUserToolsManager` Objektu umožňuje uživateli nebo vývojáři přidat nové uživatelské nástroje do aplikace. Podporuje provádění příkazů přidružených s uživatelskými nástroji a také uloží informace o nástrojích pro uživatele v registru Windows.

## <a name="syntax"></a>Syntaxe

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Vytvoří `CUserToolsManager`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|Vytvoří nový uživatelský nástroj.|
|[CUserToolsManager::FindTool](#findtool)|Vrací ukazatel `CMFCUserTool` objekt, který je přidružen ID zadaného příkazu.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Vrátí ID prostředku, který je přidružen **argumenty** nabídce **nástroje** kartě **vlastní** dialogové okno.|
|[CUserToolsManager::GetDefExt](#getdefext)|Vrátí výchozí rozšíření, která **otevřít soubor** dialogové okno ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) používá **příkaz** na **nástroje** kartě **Vlastní** dialogové okno.|
|[CUserToolsManager::GetFilter](#getfilter)|Vrací filtr souborů, které **otevřít soubor** dialogové okno ( [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md)) používá **příkaz** na **nástroje** kartě **Vlastní** dialogové okno.|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Vrátí ID prostředku, který je přidružen **výchozí adresář** nabídce **nástroje** kartě **vlastní** dialogové okno.|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Vrátí maximální počet uživatelských nástrojů, které mohou být přiděleny v aplikaci.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Vrátí Identifikátor příkazu zástupný prvek položky nabídky pro uživatele nástroje.|
|[CUserToolsManager::GetUserTools](#getusertools)|Vrátí odkaz na seznam uživatelských nástrojů.|
|[CUserToolsManager::InvokeTool](#invoketool)|Spustí aplikace přidružené k uživatelský nástroj, který má ID zadaného příkazu.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Určuje, zda ID příkazu je přidružen uživatelský nástroj.|
|[CUserToolsManager::LoadState](#loadstate)|Načte informace o nástrojích pro uživatele z registru Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Přesune zadaný uživatelský nástroj dolů v seznamu nástrojů pro uživatele.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Posune zadaný uživatelský nástroj nahoru v seznamu uživatelů nástroje.|
|[CUserToolsManager::RemoveTool](#removetool)|Nástroj pro zadaného uživatele se odebere z aplikace.|
|[CUserToolsManager::SaveState](#savestate)|Ukládá informace o nástrojích pro uživatele v registru Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Určuje výchozí rozšíření, která **otevřít soubor** dialogové okno ( [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** kartu nástroje **vlastní** dialogové okno.|
|[CUserToolsManager::SetFilter](#setfilter)|Určuje soubor filtru, který **otevřít soubor** dialogové okno ( [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** karty **Vlastní** dialogové okno.|

## <a name="remarks"></a>Poznámky

Chcete-li zahrnout uživatelské nástroje do vaší aplikace, musíte:

1. Rezervujte položky nabídky a přidružený příkaz ID pro položku nabídky Nástroje uživatele.

2. Rezervujte ID sekvenční příkazu pro každý nástroj uživatele definující uživatele ve vaší aplikaci.

3. Volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) metoda a zadat následující parametry: nabídka ID příkazu, první ID příkazu nástroj uživatel a ID poslední uživatel nástroj příkazu.

Měl by existovat pouze jeden globální `CUserToolsManager` objektu na aplikaci.

Příklad uživatelské nástroje najdete v článku VisualStudioDemo ukázkového projektu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst odkaz na `CUserToolsManager` objekt a jak vytvářet nové uživatelské nástroje. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertoolsmanager.h

##  <a name="createnewtool"></a>  CUserToolsManager::CreateNewTool

Vytvoří nový uživatelský nástroj.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený uživatelský nástroj nebo hodnota NULL, pokud počet uživatelských nástrojů byla překročena maximální délka. Vrácený typ je stejný jako typ, který je předán `CWinAppEx::EnableUserTools` jako *pToolRTC* parametru.

### <a name="remarks"></a>Poznámky

Tato metoda vyhledá první ID příkazu nabídky dostupné v rozsahu, který není zadána ve volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) a přiřadí uživatelský nástroj číslem ID této.

Metoda selže, pokud počet nástroje dosáhla maximálního počtu. K tomu dojde, když jsou přiřazeny všechny identifikátory příkazů v rámci rozsahu uživatelské nástroje. Maximální počet nástroje můžete načíst pomocí volání [CUserToolsManager::GetMaxTools](#getmaxtools). Můžete získat přístup k seznamu nástroje voláním [CUserToolsManager::GetUserTools](#getusertools) metody.

##  <a name="cusertoolsmanager"></a>  CUserToolsManager::CUserToolsManager

Vytvoří `CUserToolsManager`. Každá aplikace musí mít maximálně jeden správce nástroje uživatelů.

```
CUserToolsManager();


CUserToolsManager(
    const UINT uiCmdToolsDummy,
    const UINT uiCmdFirst,
    const UINT uiCmdLast,
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),
    UINT uArgMenuID=0,
    UINT uInitDirMenuID=0);
```

### <a name="parameters"></a>Parametry

*uiCmdToolsDummy*<br/>
[in] Celé číslo bez znaménka, která rozhraní používá jako zástupný symbol pro Identifikátor příkazu v nabídce Nástroje pro uživatele.

*uiCmdFirst*<br/>
[in] ID příkazu pro příkaz první nástroj uživatele.

*uiCmdLast*<br/>
[in] ID příkazu pro příkaz poslední nástroj uživatele.

*pToolRTC*<br/>
[in] Třída, která [CUserToolsManager::CreateNewTool](#createnewtool) vytvoří. Pomocí této třídy, můžete použít odvozeným typem [cusertool – třída](../../mfc/reference/cusertool-class.md) místo výchozí implementaci.

*uArgMenuID*<br/>
[in] ID prostředku nabídky místní nabídka argumenty.

*uInitDirMenuID*<br/>
[in] ID prostředku nabídky Počáteční adresář místní nabídka.

### <a name="remarks"></a>Poznámky

Není volání tohoto konstruktoru. Namísto toho zavolejte metodu [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatelské nástroje a volání [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) získat ukazatel `CUserToolsManager`. Další informace najdete v tématu [uživatelem definované nástroje](../../mfc/user-defined-tools.md).

##  <a name="findtool"></a>  CUserToolsManager::FindTool

Vrací ukazatel [cusertool – třída](../../mfc/reference/cusertool-class.md) objekt, který je přidružen ID zadaného příkazu.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] Identifikátor příkazu nabídky.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cusertool – třída](../../mfc/reference/cusertool-class.md) nebo `CUserTool`-odvozenému objektu, pokud úspěchu; jinak hodnota NULL.

### <a name="remarks"></a>Poznámky

Když `FindTool` je úspěšné, vrácený typ odpovídá typu *pToolRTC* parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="getargumentsmenuid"></a>  CUserToolsManager::GetArgumentsMenuID

Vrátí ID prostředku, který je přidružen **argumenty** nabídce **nástroje** kartě **vlastní** dialogové okno.

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku nabídky.

### <a name="remarks"></a>Poznámky

*UArgMenuID* parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) určuje Identifikátor prostředku.

##  <a name="getdefext"></a>  CUserToolsManager::GetDefExt

Vrátí výchozí rozšíření, která **otevřít soubor** dialogové okno ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) používá **příkaz** na **nástroje** kartě **Vlastní** dialogové okno.

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CString` objekt, který obsahuje rozšíření.

##  <a name="getfilter"></a>  CUserToolsManager::GetFilter

Vrací filtr souborů, které **otevřít soubor** dialogové okno ( [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md)) používá **příkaz** na **nástroje** kartě **Vlastní** dialogové okno.

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CString` objekt, který obsahuje filtr.

##  <a name="getinitialdirmenuid"></a>  CUserToolsManager::GetInitialDirMenuID

Vrátí ID prostředku, který je přidružen **výchozí adresář** nabídce **nástroje** kartě **vlastní** dialogové okno.

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku nabídky.

### <a name="remarks"></a>Poznámky

Je v zadané vrácené ID *uInitDirMenuID* parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="getmaxtools"></a>  CUserToolsManager::GetMaxTools

Vrátí maximální počet uživatelských nástrojů, které mohou být přiděleny v aplikaci.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet uživatelských nástrojů, které mohou být přiděleny.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem načtení maximální počet nástroje, které mohou být přiděleny v aplikaci. Toto číslo je počet ID v rozsahu od *uiCmdFirst* prostřednictvím *uiCmdLast* parametry, které můžete předat [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

##  <a name="gettoolsentrycmd"></a>  CUserToolsManager::GetToolsEntryCmd

Vrátí Identifikátor příkazu zástupný prvek položky nabídky pro uživatele nástroje.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu zástupný symbol.

### <a name="remarks"></a>Poznámky

Pokud chcete povolit uživatelské nástroje, volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). *UiCmdToolsDummy* parametr určuje Identifikátor příkazu položka příkazu nástroje. Tato metoda vrátí ID nástroje položka příkazu. Bez ohledu na toto ID se používá v nabídce, je nahrazen seznam uživatelských nástrojů až se zobrazí v nabídce.

##  <a name="getusertools"></a>  CUserToolsManager::GetUserTools

Vrátí odkaz na seznam uživatelských nástrojů.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní odkaz [coblist – třída](../../mfc/reference/coblist-class.md) objekt, který obsahuje seznam uživatelských nástrojů.

### <a name="remarks"></a>Poznámky

Volání této metody k načtení seznamu uživatele, nástroje, které [cusertoolsmanager –](../../mfc/reference/cusertoolsmanager-class.md) udržuje objekt. Každý nástroj uživatele je reprezentován objektem typu [cusertool – třída](../../mfc/reference/cusertool-class.md) nebo typ odvozený od `CUserTool`. Typ je určená *pToolRTC* parametru při volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatelské nástroje.

##  <a name="invoketool"></a>  CUserToolsManager::InvokeTool

Spustí aplikace přidružené k uživatelský nástroj, který má ID zadaného příkazu.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] ID nabídky příkazu přidružený uživatelský nástroj.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se příkaz přidružený uživatelský nástroj provedl úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této metody ke spuštění aplikace přidružené k uživateli nástroj, který má Identifikátor příkazu určené *uiCmdId*.

##  <a name="isusertoolcmd"></a>  CUserToolsManager::IsUserToolCmd

Určuje, zda ID příkazu je přidružen uživatelský nástroj.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] ID příkazu položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadaný příkaz ID je přidružena k nástroji uživatele; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda zkontroluje, jestli ID daného příkazu, který je v rozsahu ID příkazu. Zadejte rozsah při volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatelské nástroje.

##  <a name="loadstate"></a>  CUserToolsManager::LoadState

Načte informace o nástrojích pro uživatele z registru Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Cesta klíče registru Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud stav byl načten úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda načte stav `CUserToolsManager` objektu z registru Windows.

Obvykle je není tuto metodu volat přímo. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) volá jako součást procesu inicializace pracovního prostoru.

##  <a name="movetooldown"></a>  CUserToolsManager::MoveToolDown

Přesune zadaný uživatelský nástroj dolů v seznamu nástrojů pro uživatele.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool*<br/>
[in] Určuje uživatelský nástroj přesunout.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud nástroj pro uživatele byla úspěšně; přesunout dolů jinak 0.

### <a name="remarks"></a>Poznámky

Metoda selže, pokud nástroj, který *pTool* určuje není ve vnitřním seznamu nebo pokud tento nástroj je poslední v seznamu.

##  <a name="movetoolup"></a>  CUserToolsManager::MoveToolUp

Posune zadaný uživatelský nástroj nahoru v seznamu uživatelů nástroje.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool*<br/>
[in] Určuje uživatelský nástroj přesunout.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud nástroj pro uživatele byla úspěšně; přesunout nahoru jinak 0.

### <a name="remarks"></a>Poznámky

Metoda selže, pokud nástroj, který *pTool* parametr určuje není ve vnitřním seznamu nebo pokud tento nástroj je první nástroj položky v seznamu.

##  <a name="removetool"></a>  CUserToolsManager::RemoveTool

Nástroj pro zadaného uživatele se odebere z aplikace.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pTool*<br/>
[out v] Ukazatel na uživatelský nástroj k odebrání.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud nástroj se úspěšně odebral. V opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud nástroj je úspěšně odebrána, tato metoda odstraní *pTool*.

##  <a name="savestate"></a>  CUserToolsManager::SaveState

Ukládá informace o nástrojích pro uživatele v registru Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Cesta ke klíči registru Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud státu byla uložena úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Metoda uloží aktuální stav `CUserToolsManager` objektu v registru Windows.

Obvykle není nutné tuto metodu volat přímo, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) volá automaticky jako součást procesu serializace pracovního prostoru aplikace.

##  <a name="setdefext"></a>  CUserToolsManager::SetDefExt

Určuje výchozí rozšíření, která **otevřít soubor** dialogové okno ( [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** kartu nástroje **vlastní** dialogové okno.

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Parametry

*strDefExt*<br/>
[in] Textový řetězec, který obsahuje výchozí přípona názvu souboru.

### <a name="remarks"></a>Poznámky

Voláním této metody lze zadat výchozí přípona názvu souboru v **otevřít soubor** dialogové okno, které se zobrazí, když uživatel vybere aplikaci přidružit uživatelský nástroj. Výchozí hodnota je "řetězec exe".

##  <a name="setfilter"></a>  CUserToolsManager::SetFilter

Určuje soubor filtru, který **otevřít soubor** dialogové okno ( [cfiledialog – třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** karty **Vlastní** dialogové okno.

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Parametry

*strFilter*<br/>
[in] Určuje filtr.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)<br/>
[CUserTool – třída](../../mfc/reference/cusertool-class.md)
