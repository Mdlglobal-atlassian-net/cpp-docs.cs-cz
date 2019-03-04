---
title: Ccommandlineinfo – třída
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
ms.openlocfilehash: 6e4b535da00fdcecf4ce52fad696cb5d2bc55efa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303024"
---
# <a name="ccommandlineinfo-class"></a>Ccommandlineinfo – třída

Pomáhá při analýze příkazového řádku při spuštění aplikace.

## <a name="syntax"></a>Syntaxe

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|Vytvoří výchozí `CCommandLineInfo` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|Přepsání tohoto zpětného volání k analýze jednotlivé parametry.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Určuje příkazový řádek `/Automation` možnost nebyla nalezena.|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Určuje příkazový řádek `/Embedding` možnost nebyla nalezena.|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Označuje, pokud by se zobrazit úvodní obrazovky.|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Označuje příkazového prostředí pro zpracování.|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Označuje ovladač název příkazu prostředí shell, je tisk; v opačném případě prázdný.|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Určuje název souboru dá otevřít nebo vytisknout; prázdný, pokud příkaz prostředí je nový nebo DDE.|
|[CCommandLineInfo::m_strPortName](#m_strportname)|Port, který určuje název příkazového prostředí je tisk; v opačném případě prázdný.|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Označuje, že tiskárna název příkazu prostředí shell, je tisk; v opačném případě prázdný.|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Označuje restartování jedinečný identifikátor pro správce restartování, pokud je správce restartování restartování aplikace.|

## <a name="remarks"></a>Poznámky

Místní instance této třídy v obvykle vytvoří aplikace knihovny MFC [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkce objektu aplikace. Tento objekt je pak předán [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), která volá opakovaně [ParseParam](#parseparam) tak, aby vyplnil `CCommandLineInfo` objektu. `CCommandLineInfo` Objekt je pak předán [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) pro zpracování argumentů příkazového řádku a příznaky.

Tento objekt lze použít k zapouzdření následujících možností příkazového řádku a parametry:

|argument příkazového řádku|Příkaz provedený|
|----------------------------|----------------------|
|*app*|Nový soubor.|
|*aplikace* název souboru|Otevřít soubor.|
|*aplikace* `/p` název souboru|Tisk souboru se výchozí tiskárna.|
|*aplikace* `/pt` filename port ovladače tiskárny|Tisk souboru na zadané tiskárně.|
|*app* `/dde`|Spuštění a operátoru await příkazu DDE.|
|*app* `/Automation`|Spuštění jako server automatizace OLE.|
|*app* `/Embedding`|Spuštění upravit vložené položky OLE.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informuje o tom aplikace k provádění úloh registrace.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informuje o tom aplikace provádět všechny úlohy zrušení registrace.|

Odvodit novou třídu z `CCommandLineInfo` ostatní příznaky a hodnoty parametrů. Přepsat [ParseParam](#parseparam) ke zpracování nového příznaky.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo

Tento konstruktor vytvoří `CCommandLineInfo` objektu s výchozími hodnotami.

```
CCommandLineInfo();
```

### <a name="remarks"></a>Poznámky

Výchozí hodnota je chcete zobrazit úvodní obrazovku ( `m_bShowSplash=TRUE`) a ke spuštění příkazu Nový v nabídce Soubor ( `m_nShellCommand` **= NewFile**).

Volání rozhraní framework aplikace [ParseParam](#parseparam) tak, aby vyplnil datové členy tohoto objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated

Označuje, že `/Automation` příznak nebyl nalezen v příkazovém řádku.

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>Poznámky

Při hodnotě TRUE se to znamená, že spuštění jako server automatizace OLE.

##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded

Označuje, že `/Embedding` příznak nebyl nalezen v příkazovém řádku.

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>Poznámky

Při hodnotě TRUE se to znamená, že spuštění pro úpravy vložené položky OLE.

##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash

Indikuje, že se má zobrazovat úvodní obrazovka.

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>Poznámky

Pokud je hodnota TRUE, to znamená, že má být zobrazena na úvodní obrazovce pro tuto aplikaci při spuštění. Výchozí implementace [ParseParam](#parseparam) nastaví na TRUE, pokud tomuto datovému členu [m_nShellCommand](#m_nshellcommand) rovná `CCommandLineInfo::FileNew`.

##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand

Označuje příkazového prostředí pro tuto instanci aplikace.

```
m_nShellCommand;
```

### <a name="remarks"></a>Poznámky

Typ pro tento datový člen je následující Výčtový typ, který je definován v `CCommandLineInfo` třídy.

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

Stručný popis tyto hodnoty najdete v následujícím seznamu.

- `CCommandLineInfo::FileNew` Označuje, že na příkazovém řádku nebyl nalezen žádný název souboru.

- `CCommandLineInfo::FileOpen` Označuje, že název souboru byl nalezen v příkazovém řádku a že žádný z následujících příznaků nebyly nalezeny v příkazovém řádku: `/p`, `/pt`, `/dde`.

- `CCommandLineInfo::FilePrint` Označuje, že `/p` příznak nebyl nalezen v příkazovém řádku.

- `CCommandLineInfo::FilePrintTo` Označuje, že `/pt` příznak nebyl nalezen v příkazovém řádku.

- `CCommandLineInfo::FileDDE` Označuje, že `/dde` příznak nebyl nalezen v příkazovém řádku.

- `CCommandLineInfo::AppRegister` Označuje, že `/Register` nebo `/Regserver` příznak nebyl nalezen v příkazovém řádku a aplikace se zobrazí výzva k registraci.

- `CCommandLineInfo::AppUnregister` Označuje, že `/Unregister` nebo `/Unregserver` aplikace byl požádán o zrušení registrace.

- `CCommandLineInfo::RestartByRestartManager` Označuje, že aplikace byl restartován správcem restartování.

- `CCommandLineInfo::FileNothing` Vypne zobrazení při spuštění nové podřízené okno MDI. Návrh aplikace vygenerované Průvodcem aplikace MDI zobrazit nové podřízené okno při spuštění. Chcete-li tuto funkci vypnout, můžete použít aplikaci `CCommandLineInfo::FileNothing` jako příkaz prostředí při volání [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand` je volán `InitInstance( )` všech `CWinApp` odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName

Uloží hodnotu třetí parametr není příznak na příkazovém řádku.

```
CString m_strDriverName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název ovladače tiskárny pro tisk do příkazu prostředí. Výchozí implementace [ParseParam](#parseparam) nastaví tento datový člen pouze tehdy, pokud `/pt` příznak nebyl nalezen v příkazovém řádku.

##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName

Uloží hodnotu prvního parametru bez příznaku na příkazovém řádku.

```
CString m_strFileName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název souboru, který se otevře.

##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName

Uloží hodnotu čtvrtého parametru bez příznaku na příkazovém řádku.

```
CString m_strPortName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název port tiskárny pro tisk do příkazu prostředí. Výchozí implementace [ParseParam](#parseparam) nastaví tento datový člen pouze tehdy, pokud `/pt` příznak nebyl nalezen v příkazovém řádku.

##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName

Uloží hodnotu druhého parametru bez příznaku na příkazovém řádku.

```
CString m_strPrinterName;
```

### <a name="remarks"></a>Poznámky

Tento parametr je obvykle název tiskárny pro tisk do příkazu prostředí. Výchozí implementace [ParseParam](#parseparam) nastaví tento datový člen pouze tehdy, pokud `/pt` příznak nebyl nalezen v příkazovém řádku.

##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier

Jedinečné restartujte identifikátor na příkazovém řádku.

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>Poznámky

Identifikátor restartování je jedinečný pro každou instanci aplikace.

Pokud správce restartování aplikace se ukončí a je konfigurováno jeho ji restartovat, provede správce restartování aplikace z příkazového řádku s identifikátorem restartování jako volitelný parametr. Po restartování správce používá identifikátor restartování, můžete aplikaci znovu otevřít dříve otevřené dokumenty a automaticky uložené soubory obnovit.

##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam

Rozhraní volá tuto funkci k analýze/interpretaci jednotlivé parametry z příkazového řádku. Druhá verze se liší od první jenom v projektech kódování Unicode.

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

*bFlag*<br/>
Určuje, zda *pszParam* je parametr nebo příznak.

*Dosah*<br/>
Označuje, zda toto je poslední parametr nebo příznak na příkazovém řádku.

### <a name="remarks"></a>Poznámky

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) volání `ParseParam` jednou pro každý parametr nebo příznak na příkazovém řádku předání argumentu *pszParam*. Pokud je první znak parametru " **-**"nebo" **/**", pak se odebere a *bFlag* nastavena na hodnotu TRUE. Při analýze posledního parametru *výbuchu* je nastavena na hodnotu TRUE.

Výchozí implementace této funkce rozpoznává následující příznaky: `/p`, `/pt`, `/dde`, `/Automation`, a `/Embedding`, jak je znázorněno v následující tabulce:

|argument příkazového řádku|Příkaz provedený|
|----------------------------|----------------------|
|*app*|Nový soubor.|
|*aplikace* název souboru|Otevřít soubor.|
|*aplikace* `/p` název souboru|Tisk souboru se výchozí tiskárna.|
|*aplikace* `/pt` filename port ovladače tiskárny|Tisk souboru na zadané tiskárně.|
|*app* `/dde`|Spuštění a operátoru await příkazu DDE.|
|*app* `/Automation`|Spuštění jako server automatizace OLE.|
|*app* `/Embedding`|Spuštění upravit vložené položky OLE.|
|*app* `/Register`<br /><br /> *app* `/Regserver`|Informuje o tom aplikace k provádění úloh registrace.|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|Informuje o tom aplikace provádět všechny úlohy zrušení registrace.|

Tyto informace jsou uloženy v [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), a [m_nShellCommand](#m_nshellcommand). Příznaky jsou označeny buď lomítko " **/**"nebo" **-**".

Výchozí implementace umístí do první parametr bez příznaku [m_strFileName](#m_strfilename). V případě třídy `/pt` příznak, výchozí implementace vloží sekundy, třetím a čtvrtém parametry bez příznaku do [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), a [m_ strPortName](#m_strportname)v uvedeném pořadí.

Výchozí implementace také nastaví [m_bShowSplash](#m_bshowsplash) na hodnotu TRUE pouze v případě nový soubor. V případě nový soubor uživatel provedl, zahrnující samotná aplikace. Ve všech ostatních případech otevřete existující soubory pomocí prostředí, včetně zahrnuje akce uživatele přímo souboru. V hlediska zaměřené na dokument úvodní obrazovka nemusí oznámit spuštění aplikace.

Přepsání této funkce ve vaší odvozené třídy za účelem zpracování další příznak a parametr hodnoty.

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)
