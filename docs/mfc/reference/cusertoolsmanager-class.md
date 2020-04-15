---
title: CUserToolsManager – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: c1f14657350c08679868299ce4878cca2ae10eec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373229"
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager – třída

Udržuje kolekci [CUserTool třídy](../../mfc/reference/cusertool-class.md) objektů v aplikaci. Uživatelský nástroj je položka nabídky, která spouští externí aplikaci. Objekt `CUserToolsManager` umožňuje uživateli nebo vývojáři přidat do aplikace nové uživatelské nástroje. Podporuje provádění příkazů spojených s uživatelskými nástroji a také ukládá informace o uživatelských nástrojích v registru systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CUserToolsManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Vytvoří `CUserToolsManager`.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CUserToolsManager::CreateNewTool](#createnewtool)|Vytvoří nový uživatelský nástroj.|
|[CUserToolsManager::FindTool](#findtool)|Vrátí ukazatel na `CMFCUserTool` objekt, který je přidružen k zadanému ID příkazu.|
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Vrátí ID prostředku, které je přidruženo k nabídce **Argumenty** na kartě **Nástroje** v dialogovém okně **Přizpůsobit.**|
|[CUserToolsManager::GetDefExt](#getdefext)|Vrátí výchozí příponu, kterou dialogové okno **Otevřít soubor** [(CFileDialog)](../../mfc/reference/cfiledialog-class.md#cfiledialog)používá v **poli Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**|
|[CUserToolsManager::GetFilter](#getfilter)|Vrátí filtr souborů, který používá dialogové okno **Otevřít soubor** ( [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md)) v poli **Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**|
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Vrátí ID prostředku přidružené k nabídce **Počáteční adresář** na kartě **Nástroje** v dialogovém okně **Přizpůsobit.**|
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Vrátí maximální počet uživatelských nástrojů, které mohou být přiděleny v aplikaci.|
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Vrátí ID příkazu zástupného symbolu položky nabídky pro uživatelské nástroje.|
|[CUserToolsManager::GetUserTools](#getusertools)|Vrátí odkaz na seznam uživatelských nástrojů.|
|[CUserToolsManager::InvokeTool](#invoketool)|Spustí aplikaci přidruženou k uživatelskému nástroji, který má zadané ID příkazu.|
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Určuje, zda je ID příkazu přidruženo k nástroji uživatele.|
|[CUserToolsManager::LoadState](#loadstate)|Načte informace o uživatelských nástrojích z registru systému Windows.|
|[CUserToolsManager::MoveToolDown](#movetooldown)|Přesune zadaný uživatelský nástroj dolů v seznamu uživatelských nástrojů.|
|[CUserToolsManager::MoveToolUp](#movetoolup)|Přesune zadaný uživatelský nástroj v seznamu uživatelských nástrojů nahoru.|
|[CUserToolsManager::Nástroj pro odstranění](#removetool)|Odebere zadaný uživatelský nástroj z aplikace.|
|[CUserToolsManager::Uložitstav](#savestate)|Ukládá informace o uživatelských nástrojích v registru systému Windows.|
|[CUserToolsManager::SetDefExt](#setdefext)|Určuje výchozí příponu, kterou dialogové okno **Otevření souboru** [(třída CFileDialog](../../mfc/reference/cfiledialog-class.md)) používá v poli **Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**|
|[CUserToolsManager::SetFilter](#setfilter)|Určuje filtr souborů, který používá dialogové okno **Otevřít soubor** ( [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md)) v poli **Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**|

## <a name="remarks"></a>Poznámky

Chcete-li do aplikace začlenit uživatelské nástroje, musíte:

1. Rezervujte položku nabídky a přidružené ID příkazu pro položku nabídky uživatelského nástroje.

2. Vyhraďte id sekvenčního příkazu pro každý uživatelský nástroj, který může uživatel definovat ve vaší aplikaci.

3. Zavolejte metodu [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) a zařazujte následující parametry: ID příkazu nabídky, ID příkazu prvního uživatelského nástroje a ID posledního příkazu uživatelského nástroje.

V jedné aplikaci `CUserToolsManager` by měl existovat pouze jeden globální objekt.

Příklad uživatelských nástrojů naleznete v ukázkovém projektu VisualStudioDemo.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst `CUserToolsManager` odkaz na objekt a jak vytvořit nové uživatelské nástroje. Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CUserToolsManager`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxusertoolsmanager.h

## <a name="cusertoolsmanagercreatenewtool"></a><a name="createnewtool"></a>CUserToolsManager::CreateNewTool

Vytvoří nový uživatelský nástroj.

```
CUserTool* CreateNewTool();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený uživatelský nástroj nebo NULL, pokud počet uživatelských nástrojů překročil maximum. Vrácený typ je stejný jako typ, `CWinAppEx::EnableUserTools` který je předán jako parametr *pToolRTC.*

### <a name="remarks"></a>Poznámky

Tato metoda vyhledá první id příkazu nabídky k dispozici v rozsahu, který je dodáván ve volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) a přiřadí uživatelský nástroj toto ID.

Metoda se nezdaří, pokud počet nástrojů dosáhl maxima. K tomu dochází, když jsou všechny ID příkazů v rozsahu přiřazeny uživatelským nástrojům. Maximální počet nástrojů můžete načíst voláním [CUserToolsManager::GetMaxTools](#getmaxtools). Přístup k seznamu nástrojů můžete získat voláním metody [CUserToolsManager::GetUserTools.](#getusertools)

## <a name="cusertoolsmanagercusertoolsmanager"></a><a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager

Vytvoří `CUserToolsManager`. Každá aplikace musí mít maximálně jeden správce uživatelských nástrojů.

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
[v] Nepodepsané celé číslo, které rozhraní používá jako zástupný symbol pro ID příkazu nabídky uživatelských nástrojů.

*uiCmdPrvní*<br/>
[v] ID příkazu pro první příkaz uživatelského nástroje.

*uiCmdLast*<br/>
[v] ID příkazu pro poslední příkaz uživatelského nástroje.

*pToolRTC*<br/>
[v] Třída, která [CUserToolsManager::CreateNewTool](#createnewtool) vytvoří. Pomocí této třídy můžete použít odvozený typ [CUserTool Class](../../mfc/reference/cusertool-class.md) namísto výchozí implementace.

*uArgMenuID*<br/>
[v] ID prostředku nabídky místní nabídky argumentů.

*uInitDirMenuID*<br/>
[v] ID prostředku nabídky v místní nabídce adresáře.

### <a name="remarks"></a>Poznámky

Nevolat tento konstruktor. Místo toho zavolejte [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatelské nástroje a volání [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) získat ukazatel na `CUserToolsManager`. Další informace naleznete v [tématu Nástroje definované uživatelem](../../mfc/user-defined-tools.md).

## <a name="cusertoolsmanagerfindtool"></a><a name="findtool"></a>CUserToolsManager::FindTool

Vrátí ukazatel na objekt [CUserTool Class,](../../mfc/reference/cusertool-class.md) který je přidružen k zadanému ID příkazu.

```
CUserTool* FindTool(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[v] Identifikátor příkazu nabídky.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [CUserTool třídy](../../mfc/reference/cusertool-class.md) nebo `CUserTool`odvozený objekt, pokud úspěch; jinak NULL.

### <a name="remarks"></a>Poznámky

Když `FindTool` je úspěšný, vrácený typ je stejný jako typ parametru *pToolRTC* [cWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetargumentsmenuid"></a><a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID

Vrátí ID prostředku, které je přidruženo k nabídce **Argumenty** na kartě **Nástroje** v dialogovém okně **Přizpůsobit.**

```
UINT GetArgumentsMenuID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku nabídky.

### <a name="remarks"></a>Poznámky

Parametr *uArgMenuID* [cWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) určuje ID prostředku.

## <a name="cusertoolsmanagergetdefext"></a><a name="getdefext"></a>CUserToolsManager::GetDefExt

Vrátí výchozí příponu, kterou dialogové okno **Otevřít soubor** [(CFileDialog)](../../mfc/reference/cfiledialog-class.md#cfiledialog)používá v **poli Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**

```
const CString& GetDefExt() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CString` objekt, který obsahuje rozšíření.

## <a name="cusertoolsmanagergetfilter"></a><a name="getfilter"></a>CUserToolsManager::GetFilter

Vrátí filtr souborů, který používá dialogové okno **Otevřít soubor** ( [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md)) v poli **Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**

```
const CString& GetFilter() const;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `CString` objekt, který obsahuje filtr.

## <a name="cusertoolsmanagergetinitialdirmenuid"></a><a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID

Vrátí ID prostředku přidružené k nabídce **Počáteční adresář** na kartě **Nástroje** v dialogovém okně **Přizpůsobit.**

```
UINT GetInitialDirMenuID() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor prostředku nabídky.

### <a name="remarks"></a>Poznámky

Vrácené ID je zadáno v parametru *uInitDirMenuID* [cWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergetmaxtools"></a><a name="getmaxtools"></a>CUserToolsManager::GetMaxTools

Vrátí maximální počet uživatelských nástrojů, které mohou být přiděleny v aplikaci.

```
int GetMaxTools() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet uživatelských nástrojů, které mohou být přiděleny.

### <a name="remarks"></a>Poznámky

Volání této metody načíst maximální počet nástrojů, které mohou být přiděleny v aplikaci. Toto číslo je počet ID v rozsahu od *uiCmdFirst* až *po parametry uiCmdLast,* které předáte [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).

## <a name="cusertoolsmanagergettoolsentrycmd"></a><a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd

Vrátí ID příkazu zástupného symbolu položky nabídky pro uživatelské nástroje.

```
UINT GetToolsEntryCmd() const;
```

### <a name="return-value"></a>Návratová hodnota

ID příkazu zástupného symbolu.

### <a name="remarks"></a>Poznámky

Chcete-li povolit uživatelské nástroje, volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). Parametr *uiCmdToolsDummy* určuje ID příkazu příkazu pro zadání nástroje. Tato metoda vrátí ID příkazu pro zadání nástroje. Všude tam, kde je toto ID použito v nabídce, je nahrazeno seznamem uživatelských nástrojů, když se zobrazí nabídka.

## <a name="cusertoolsmanagergetusertools"></a><a name="getusertools"></a>CUserToolsManager::GetUserTools

Vrátí odkaz na seznam uživatelských nástrojů.

```
const CObList& GetUserTools() const;
```

### <a name="return-value"></a>Návratová hodnota

Const odkaz na [CObList Class](../../mfc/reference/coblist-class.md) objekt, který obsahuje seznam uživatelských nástrojů.

### <a name="remarks"></a>Poznámky

Volání této metody načíst seznam uživatelských nástrojů, které udržuje [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) objektudržuje. Každý uživatelský nástroj je reprezentován objektem typu [CUserTool](../../mfc/reference/cusertool-class.md) `CUserTool`Class nebo typem odvozeným z . Typ je určen parametrem *pToolRTC* při volání [CWinAppEx::EnableUserTools,](../../mfc/reference/cwinappex-class.md#enableusertools) aby bylo možné povolit uživatelské nástroje.

## <a name="cusertoolsmanagerinvoketool"></a><a name="invoketool"></a>CUserToolsManager::InvokeTool

Spustí aplikaci přidruženou k uživatelskému nástroji, který má zadané ID příkazu.

```
BOOL InvokeTool(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[v] ID příkazu nabídky přidružené k uživatelskému nástroji.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl příkaz přidružený k uživatelskému nástroji úspěšně proveden; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této metody ke spuštění aplikace přidružené k uživatelskému nástroji, který má ID příkazu určené *uiCmdId*.

## <a name="cusertoolsmanagerisusertoolcmd"></a><a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd

Určuje, zda je ID příkazu přidruženo k nástroji uživatele.

```
BOOL IsUserToolCmd(UINT uiCmdId) const;
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[v] ID příkazu položky nabídky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je dané ID příkazu přidruženo k nástroji uživatele; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda zkontroluje, zda je dané ID příkazu v rozsahu ID příkazu. Rozsah zadáte při volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatelské nástroje.

## <a name="cusertoolsmanagerloadstate"></a><a name="loadstate"></a>CUserToolsManager::LoadState

Načte informace o uživatelských nástrojích z registru systému Windows.

```
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Cesta ke klíči registru systému Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl stav úspěšně načten; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda načte `CUserToolsManager` stav objektu z registru systému Windows.

Obvykle není volání této metody přímo. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) jej volá jako součást procesu inicializace pracovního prostoru.

## <a name="cusertoolsmanagermovetooldown"></a><a name="movetooldown"></a>CUserToolsManager::MoveToolDown

Přesune zadaný uživatelský nástroj dolů v seznamu uživatelských nástrojů.

```
BOOL MoveToolDown(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pNástroj*<br/>
[v] Určuje uživatelský nástroj, který se má přesunout.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl uživatelský nástroj úspěšně přesunut dolů; jinak 0.

### <a name="remarks"></a>Poznámky

Metoda se nezdaří, pokud nástroj, který *určuje pTool* není ve vnitřním seznamu nebo pokud je nástroj poslední v seznamu.

## <a name="cusertoolsmanagermovetoolup"></a><a name="movetoolup"></a>CUserToolsManager::MoveToolUp

Přesune zadaný uživatelský nástroj v seznamu uživatelských nástrojů nahoru.

```
BOOL MoveToolUp(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pNástroj*<br/>
[v] Určuje uživatelský nástroj, který se má přesunout.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl uživatelský nástroj úspěšně přesunut nahoru; jinak 0.

### <a name="remarks"></a>Poznámky

Metoda se nezdaří, pokud nástroj, který určuje parametr *pTool,* není ve vnitřním seznamu nebo pokud je nástroj první položkou nástroje v seznamu.

## <a name="cusertoolsmanagerremovetool"></a><a name="removetool"></a>CUserToolsManager::Nástroj pro odstranění

Odebere zadaný uživatelský nástroj z aplikace.

```
BOOL RemoveTool(CUserTool* pTool);
```

### <a name="parameters"></a>Parametry

*pNástroj*<br/>
[dovnitř, ven] Ukazatel na uživatelský nástroj, který má být odebrán.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je nástroj úspěšně odebrán. V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud je nástroj úspěšně odebrán, tato metoda odstraní *pTool*.

## <a name="cusertoolsmanagersavestate"></a><a name="savestate"></a>CUserToolsManager::Uložitstav

Ukládá informace o uživatelských nástrojích v registru systému Windows.

```
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[v] Cesta ke klíči registru systému Windows.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl stav úspěšně uložen; jinak 0.

### <a name="remarks"></a>Poznámky

Metoda ukládá aktuální stav `CUserToolsManager` objektu v registru systému Windows.

Obvykle není nutné volat tuto metodu přímo, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) volá automaticky jako součást procesu serializace pracovního prostoru aplikace.

## <a name="cusertoolsmanagersetdefext"></a><a name="setdefext"></a>CUserToolsManager::SetDefExt

Určuje výchozí příponu, kterou dialogové okno **Otevření souboru** [(třída CFileDialog](../../mfc/reference/cfiledialog-class.md)) používá v poli **Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**

```
void SetDefExt(const CString& strDefExt);
```

### <a name="parameters"></a>Parametry

*strDefExt*<br/>
[v] Textový řetězec, který obsahuje výchozí příponu názvu souboru.

### <a name="remarks"></a>Poznámky

Voláním této metody určete výchozí příponu názvu souboru v dialogovém okně **Otevřít soubor,** která se zobrazí, když uživatel vybere aplikaci, kterou má přidružit k nástroji uživatele. Výchozí hodnota je "exe".

## <a name="cusertoolsmanagersetfilter"></a><a name="setfilter"></a>CUserToolsManager::SetFilter

Určuje filtr souborů, který používá dialogové okno **Otevřít soubor** ( [Třída CFileDialog](../../mfc/reference/cfiledialog-class.md)) v poli **Příkaz** na kartě **Nástroje** dialogového okna **Přizpůsobit.**

```
void SetFilter(const CString& strFilter);
```

### <a name="parameters"></a>Parametry

*strFilter*<br/>
[v] Určuje filtr.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Třída CUserTool](../../mfc/reference/cusertool-class.md)
