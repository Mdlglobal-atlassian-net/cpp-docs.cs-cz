---
title: Třída CCommandLineInfo
ms.date: 11/04/2016
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
ms.openlocfilehash: 0b4d5e5d253f2eb10388a69286d21e2190826eba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369464"
---
# <a name="ccommandlineinfo-class"></a>Třída CCommandLineInfo

Pomáhá při analýzě příkazového řádku při spuštění aplikace.

## <a name="syntax"></a>Syntaxe

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Vytvoří výchozí `CCommandLineInfo` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Přepište toto zpětné volání analyzovat jednotlivé parametry.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Označuje, že `/Automation` byla nalezena možnost příkazového řádku.|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Označuje, že `/Embedding` byla nalezena možnost příkazového řádku.|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Označuje, zda má být zobrazena úvodní obrazovka.|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Označuje příkaz prostředí, který má být zpracován.|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Označuje název ovladače, pokud je příkaz prostředí Print To; jinak prázdné.|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Označuje název souboru, který má být otevřen nebo vytištěn; prázdné, pokud je příkaz prostředí Nový nebo DDE.|
|[CCommandLineInfo::m_strPortName](#m_strportname)|Označuje název portu, pokud je příkaz prostředí Print To; jinak prázdné.|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Označuje název tiskárny, pokud je příkaz prostředí Print To; jinak prázdné.|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Označuje jedinečný identifikátor restartování pro správce restartování, pokud správce restartování restartoval aplikaci.|

## <a name="remarks"></a>Poznámky

Aplikace knihovny MFC obvykle vytvoří místní instanci této třídy ve funkci [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) jejího aplikačního objektu. Tento objekt je pak předán [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), který opakovaně volá `CCommandLineInfo` [ParseParam](#parseparam) vyplnit objekt. Objekt `CCommandLineInfo` je pak předán [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) pro zpracování argumentů a příznaků příkazového řádku.

Tento objekt můžete použít k zapouzdření následujících možností a parametrů příkazového řádku:

|Argument příkazového řádku|Příkaz proveden|
|----------------------------|----------------------|
|*App*|Nový soubor.|
|název souboru *aplikace*|Otevřete soubor.|
|název souboru *aplikace* `/p`|Tisk souboru na výchozí tiskárnu.|
|Port ovladače tiskárny se názvem *souboru aplikace* `/pt`|Tisk souboru na určené tiskárně.|
|*aplikace*`/dde`|Spusťte a počkejte na příkaz DDE.|
|*aplikace*`/Automation`|Spusťte jako server automatizace OLE.|
|*aplikace*`/Embedding`|Spuštěním můžete upravit vloženou položku OLE.|
|*aplikace*`/Register`<br /><br /> *aplikace*`/Regserver`|Informuje aplikaci k provedení všech registračních úkolů.|
|*aplikace*`/Unregister`<br /><br /> *aplikace*`/Unregserver`|Informuje aplikaci k provedení všech úloh zrušení registrace.|

Odvodit `CCommandLineInfo` novou třídu z pro zpracování jiných příznaků a hodnot parametrů. Přepsat [ParseParam](#parseparam) pro zpracování nových příznaků.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLineInfo::CCommandLineInfo

Tento konstruktor `CCommandLineInfo` vytvoří objekt s výchozími hodnotami.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se zobrazí `m_bShowSplash=TRUE`úvodní obrazovka ( ) a v `m_nShellCommand`nabídce Soubor se spustí příkaz Nový ( **=NewFile**).

Rozhraní aplikace volá [ParseParam](#parseparam) vyplnit datové členy tohoto objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a>CCommandLineInfo::m_bRunAutomated

Označuje, `/Automation` že příznak byl nalezen na příkazovém řádku.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Poznámky

Pokud true, to znamená spustit jako server automatizace OLE.

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a>CCommandLineInfo::m_bRunEmbedded

Označuje, `/Embedding` že příznak byl nalezen na příkazovém řádku.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Poznámky

Pokud TRUE, to znamená spuštění pro úpravy vložené položky OLE.

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a>CCommandLineInfo::m_bShowSplash

Označuje, že by měla být zobrazena úvodní obrazovka.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Poznámky

Pokud true, to znamená, že úvodní obrazovka pro tuto aplikaci by měla být zobrazena při spuštění. Výchozí implementace [ParseParam](#parseparam) nastaví tento datový člen na `CCommandLineInfo::FileNew`HODNOTU [TRUE,](#m_nshellcommand) pokud je m_nShellCommand rovno .

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a>CCommandLineInfo::m_nShellCommand

Označuje příkaz prostředí pro tuto instanci aplikace.

```
m_nShellCommand;
```

### <a name="remarks"></a>Poznámky

Typ pro tento datový člen je následující výčtový typ, `CCommandLineInfo` který je definován ve třídě.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

Stručný popis těchto hodnot naleznete v následujícím seznamu.

- `CCommandLineInfo::FileNew`Označuje, že na příkazovém řádku nebyl nalezen žádný název souboru.

- `CCommandLineInfo::FileOpen`Označuje, že na příkazovém řádku byl nalezen název souboru a že `/p` `/pt`na `/dde`příkazovém řádku nebyl nalezen žádný z následujících příznaků: , , .

- `CCommandLineInfo::FilePrint`Označuje, `/p` že příznak byl nalezen na příkazovém řádku.

- `CCommandLineInfo::FilePrintTo`Označuje, `/pt` že příznak byl nalezen na příkazovém řádku.

- `CCommandLineInfo::FileDDE`Označuje, `/dde` že příznak byl nalezen na příkazovém řádku.

- `CCommandLineInfo::AppRegister`Označuje, `/Register` že `/Regserver` příznak nebo byl nalezen na příkazovém řádku a aplikace byla požádána o registraci.

- `CCommandLineInfo::AppUnregister`Označuje, `/Unregister` že `/Unregserver` aplikace nebo byla požádána o zrušení registrace.

- `CCommandLineInfo::RestartByRestartManager`Označuje, že aplikace byla restartována správcem restartování.

- `CCommandLineInfo::FileNothing`Vypne zobrazení nového podřízeného okna MDI při spuštění. Aplikace MDI generované průvodcem aplikace podle návrhu zobrazí při spuštění nové podřízené okno. Chcete-li tuto funkci vypnout, aplikace může použít `CCommandLineInfo::FileNothing` jako příkaz prostředí při volání [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand`je volána `InitInstance( )` všechny `CWinApp` odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a>CCommandLineInfo::m_strDriverName

Uloží hodnotu třetího parametru bez vlajky na příkazovém řádku.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název ovladače tiskárny pro příkaz prostředí Print To. Výchozí implementace [ParseParam](#parseparam) nastaví tento datový `/pt` člen pouze v případě, že příznak byl nalezen na příkazovém řádku.

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a>CCommandLineInfo::m_strFileName

Uloží hodnotu prvního parametru bez vlajky na příkazovém řádku.

```
CString m_strFileName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název souboru otevřít.

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a>CCommandLineInfo::m_strPortName

Uloží hodnotu čtvrtého parametru bez vlajky na příkazovém řádku.

```
CString m_strPortName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název portu tiskárny pro příkaz prostředí Print To. Výchozí implementace [ParseParam](#parseparam) nastaví tento datový `/pt` člen pouze v případě, že příznak byl nalezen na příkazovém řádku.

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a>CCommandLineInfo::m_strPrinterName

Uloží hodnotu druhého parametru bez vlajky na příkazovém řádku.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název tiskárny pro příkaz prostředí Print To. Výchozí implementace [ParseParam](#parseparam) nastaví tento datový `/pt` člen pouze v případě, že příznak byl nalezen na příkazovém řádku.

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLineInfo::m_strRestartIdentifier

Jedinečný identifikátor restartování na příkazovém řádku.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Poznámky

Identifikátor restartování je jedinečný pro každou instanci aplikace.

Pokud správce restartování ukončí aplikaci a je nakonfigurován tak, aby ji restartoval, spustí aplikaci z příkazového řádku s identifikátorem restartu jako volitelným parametrem. Pokud správce restartování použije identifikátor restartování, aplikace může znovu otevřít dříve otevřené dokumenty a obnovit automaticky uložené soubory.

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLineInfo::ParseParam

Framework volá tuto funkci analyzovat/interpretovat jednotlivé parametry z příkazového řádku. Druhá verze se liší od první pouze v projektech Unicode.

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>Parametry

*pszParam*<br/>
Parametr nebo příznak.

*bPříznak*<br/>
Označuje, zda *pszParam* je parametr nebo příznak.

*Výbuch*<br/>
Označuje, zda se jedná o poslední parametr nebo příznak na příkazovém řádku.

### <a name="remarks"></a>Poznámky

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) `ParseParam` volá jednou pro každý parametr nebo příznak na příkazovém řádku a předá argument *pszParam*. Pokud je první znak parametru **-**" " **/** nebo " , je odebrán a *bFlag* je nastaven na HODNOTU TRUE. Při analýzě konečného parametru je *bLast* nastavena na HODNOTU TRUE.

Výchozí implementace této funkce rozpozná následující `/p`příznaky: `/dde` `/Automation`, `/pt` `/Embedding`, , a , jak je znázorněno v následující tabulce:

|Argument příkazového řádku|Příkaz proveden|
|----------------------------|----------------------|
|*App*|Nový soubor.|
|název souboru *aplikace*|Otevřete soubor.|
|název souboru *aplikace* `/p`|Tisk souboru na výchozí tiskárnu.|
|Port ovladače tiskárny se názvem *souboru aplikace* `/pt`|Tisk souboru na určené tiskárně.|
|*aplikace*`/dde`|Spusťte a počkejte na příkaz DDE.|
|*aplikace*`/Automation`|Spusťte jako server automatizace OLE.|
|*aplikace*`/Embedding`|Spuštěním můžete upravit vloženou položku OLE.|
|*aplikace*`/Register`<br /><br /> *aplikace*`/Regserver`|Informuje aplikaci k provedení všech registračních úkolů.|
|*aplikace*`/Unregister`<br /><br /> *aplikace*`/Unregserver`|Informuje aplikaci k provedení všech úloh zrušení registrace.|

Tyto informace jsou uloženy v [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded)a [m_nShellCommand](#m_nshellcommand). Příznaky jsou označeny lomítkem pro **/** lomítko nebo pomlčkou . **-**

Výchozí implementace umístí první parametr bez příznaku do [m_strFileName](#m_strfilename). `/pt` V případě příznakvýchozí implementace umístí druhý, třetí a čtvrtý non-flag parametry do [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername)a [m_strPortName](#m_strportname).

Výchozí implementace také nastaví [m_bShowSplash](#m_bshowsplash) na HODNOTU TRUE pouze v případě nového souboru. V případě nového souboru uživatel přijal opatření zahrnující samotnou aplikaci. V každém jiném případě, včetně otevření existujících souborů pomocí prostředí, akce uživatele zahrnuje soubor přímo. Z hlediska zaměření na dokument nemusí úvodní obrazovka oznamovat spuštění aplikace.

Přepsat tuto funkci v odvozené třídě pro zpracování jiných hodnot příznaku a parametrů.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
