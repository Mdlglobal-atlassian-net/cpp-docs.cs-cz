---
title: Třída CCommandLineInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43bd8f7b12eee847fd6b8784d21f4b565c7fc6a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo – třída
Pomůcek při analýze příkazového řádku při spuštění aplikace.  
  
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
|[CCommandLineInfo::ParseParam](#parseparam)|Potlačí tuto zpětného volání k analýze jednotlivé parametry.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|Určuje, na příkazovém řádku `/Automation` možnost nebyl nalezen.|  
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|Určuje, na příkazovém řádku `/Embedding` možnost nebyl nalezen.|  
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|Označuje, pokud mají být zobrazeny úvodní obrazovka.|  
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|Určuje příkaz prostředí mají být zpracovány.|  
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|Označuje ovladač název Pokud prostředí příkazu je tisk; v opačném případě prázdné.|  
|[CCommandLineInfo::m_strFileName](#m_strfilename)|Určuje název souboru, který chcete otevřít nebo vytisknout; prázdný, pokud je prostředí příkazu New nebo DDE.|  
|[CCommandLineInfo::m_strPortName](#m_strportname)|Určuje port název Pokud prostředí příkazu je tisk; v opačném případě prázdné.|  
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|Označuje tiskárny název Pokud prostředí příkazu je tisk; v opačném případě prázdné.|  
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|Označuje restartování jedinečný identifikátor pro správce restartování, pokud správce restartování restartovat aplikaci.|  
  
## <a name="remarks"></a>Poznámky  
 Aplikace MFC obvykle vytvoří místní instance této třídy v [InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkce jeho objektu application. Tento objekt byl následně předán do [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline), která opakovaně volá [ParseParam](#parseparam) k vyplnění `CCommandLineInfo` objektu. `CCommandLineInfo` Objekt byl následně předán do [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand) pro zpracování argumenty příkazového řádku a značky.  
  
 Tento objekt můžete použít k zapouzdření následujících možností příkazového řádku a parametry:  
  
|Argument příkazového řádku|Příkaz proveden|  
|----------------------------|----------------------|  
|*Aplikace*|Nový soubor.|  
|*aplikace* filename|Otevření souboru.|  
|*aplikace* `/p` filename|Tisk souboru na výchozí tiskárnu.|  
|*aplikace* `/pt` filename port ovladačů tiskárny|Tisk souboru do zadané tiskárny.|  
|*Aplikace* `/dde`|Spuštění a operátoru await DDE příkaz.|  
|*Aplikace* `/Automation`|Spuštění jako serveru automatizace OLE.|  
|*Aplikace* `/Embedding`|Spuštění k úpravě vložené položky OLE.|  
|*Aplikace* `/Register`<br /><br /> *Aplikace* `/Regserver`|Informuje o aplikace k provádění úloh registrace.|  
|*Aplikace* `/Unregister`<br /><br /> *Aplikace* `/Unregserver`|Informuje o aplikace k provádění úloh zrušení registrace.|  
  
 Odvození nové třídy z `CCommandLineInfo` pro zpracování ostatní příznaky a hodnoty parametrů. Přepsání [ParseParam](#parseparam) zpracovat nové příznaků.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo  
 Tento konstruktor vytvoří `CCommandLineInfo` objektu s výchozími hodnotami.  
  
```  
CCommandLineInfo();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení se zobrazí úvodní obrazovka ( `m_bShowSplash=TRUE`) a spusťte nový příkaz v nabídce Soubor ( `m_nShellCommand` **= NewFile**).  
  
 Volání framework aplikace [ParseParam](#parseparam) k vyplnění datové členy tohoto objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]  
  
##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated  
 Určuje, že `/Automation` příznak byl nalezen na příkazovém řádku.  
  
```  
BOOL m_bRunAutomated;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, to znamená, že spuštění jako serveru automatizace OLE.  
  
##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded  
 Určuje, že `/Embedding` příznak byl nalezen na příkazovém řádku.  
  
```  
BOOL m_bRunEmbedded;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, to znamená, že spuštění úpravy vložené položky OLE.  
  
##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash  
 Určuje, zda mají být zobrazeny úvodní obrazovka.  
  
```  
BOOL m_bShowSplash;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud `TRUE`, to znamená úvodní obrazovka pro tuto aplikaci, které mají být zobrazeny během spouštění. Výchozí implementaci [ParseParam](#parseparam) nastaví tento člen dat `TRUE` Pokud [m_nShellCommand](#m_nshellcommand) rovná `CCommandLineInfo::FileNew`.  
  
##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand  
 Určuje příkaz prostředí pro tuto instanci aplikace.  
  
```  
m_nShellCommand;  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ pro tento člen dat je následující výčtového typu, která je definována v `CCommandLineInfo` třídy.  
  
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
  
- `CCommandLineInfo::FileOpen` Určuje, že na příkazovém řádku byl nalezen název souboru a že žádný z následujících příznaků nebyly nalezeny v příkazovém řádku: `/p`, `/pt`, `/dde`.  
  
- `CCommandLineInfo::FilePrint` Určuje, že `/p` příznak byl nalezen na příkazovém řádku.  
  
- `CCommandLineInfo::FilePrintTo` Určuje, že `/pt` příznak byl nalezen na příkazovém řádku.  
  
- `CCommandLineInfo::FileDDE` Určuje, že `/dde` příznak byl nalezen na příkazovém řádku.  
  
- `CCommandLineInfo::AppRegister` Určuje, že `/Register` nebo `/Regserver` příznak byl nalezen na příkazovém řádku a aplikace se zobrazí výzva k registraci.  
  
- `CCommandLineInfo::AppUnregister` Určuje, že `/Unregister` nebo `/Unregserver` byla požádána se zrušit registraci.  
  
- `CCommandLineInfo::RestartByRestartManager` Označuje, že aplikace byla restartovat správce restartování.  
  
- `CCommandLineInfo::FileNothing` Vypne zobrazení nového podřízeného okna MDI při spuštění. Návrh aplikace generované v Průvodci aplikace MDI zobrazení nového podřízeného okna při spuštění. Chcete-li tuto funkci vypnout, můžete použít aplikaci `CCommandLineInfo::FileNothing` jako příkaz prostředí při volání [ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand). `ProcessShellCommand` volá `InitInstance( )` všech `CWinApp` odvozených třídách.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]  
  
##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName  
 Ukládá hodnotu identifikátoru třetí parametr není příznak na příkazovém řádku.  
  
```  
CString m_strDriverName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento parametr je obvykle název ovladače tiskárny pro tisk do prostředí příkazu. Výchozí implementaci [ParseParam](#parseparam) nastaví tato data člena jenom Pokud `/pt` příznak byl nalezen na příkazovém řádku.  
  
##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName  
 Ukládá hodnotu prvního parametru bez příznaku na příkazovém řádku.  
  
```  
CString m_strFileName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento parametr je obvykle název otevření souboru.  
  
##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName  
 Ukládá hodnotu čtvrtého parametru bez příznaku na příkazovém řádku.  
  
```  
CString m_strPortName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento parametr je obvykle název port tiskárny pro tisk do prostředí příkazu. Výchozí implementaci [ParseParam](#parseparam) nastaví tato data člena jenom Pokud `/pt` příznak byl nalezen na příkazovém řádku.  
  
##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName  
 Ukládá hodnotu identifikátoru druhý parametr není příznak na příkazovém řádku.  
  
```  
CString m_strPrinterName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento parametr je obvykle název tiskárny pro tisk do prostředí příkazu. Výchozí implementaci [ParseParam](#parseparam) nastaví tato data člena jenom Pokud `/pt` příznak byl nalezen na příkazovém řádku.  
  
##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier  
 Jedinečný restartujte identifikátor na příkazovém řádku.  
  
```  
CString m_strRestartIdentifier;  
```  
  
### <a name="remarks"></a>Poznámky  
 Restartování identifikátor je jedinečný pro každou instanci aplikace.  
  
 Pokud správce restartování ukončí aplikaci a nastaven tak, aby ji restartovat, provede správce restartování aplikace z příkazového řádku s identifikátorem restartování jako volitelný parametr. Při restartování správce používá identifikátor restartování, může aplikace otevřete dříve otevřené dokumenty a obnovit soubory automaticky uloženo.  
  
##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam  
 Rozhraní framework volá tuto funkci analýzy nebo interpretovat jednotlivé parametry z příkazového řádku. Druhá verze se liší od prvního jenom v projektech kódování Unicode.  
  
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
 `pszParam`  
 Parametr nebo příznak.  
  
 *bFlag*  
 Určuje, zda `pszParam` parametr nebo příznak.  
  
 `bLast`  
 Určuje, zda toto je poslední parametr nebo příznak na příkazovém řádku.  
  
### <a name="remarks"></a>Poznámky  
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline) volání `ParseParam` jednou pro každý parametr nebo příznak na příkazovém řádku předání argumentu `pszParam`. Pokud je první znak parametru ' **-**'nebo' **/**", pak se odebere a *bFlag* je nastaven na `TRUE`. Při analýze konečný parametr `bLast` je nastaven na `TRUE`.  
  
 Výchozí implementace této funkce rozpozná následující příznaky: `/p`, `/pt`, `/dde`, `/Automation`, a `/Embedding`, jak je znázorněno v následující tabulce:  
  
|Argument příkazového řádku|Příkaz proveden|  
|----------------------------|----------------------|  
|*Aplikace*|Nový soubor.|  
|*aplikace* filename|Otevření souboru.|  
|*aplikace* `/p` filename|Tisk souboru na výchozí tiskárnu.|  
|*aplikace* `/pt` filename port ovladačů tiskárny|Tisk souboru do zadané tiskárny.|  
|*Aplikace* `/dde`|Spuštění a operátoru await DDE příkaz.|  
|*Aplikace* `/Automation`|Spuštění jako serveru automatizace OLE.|  
|*Aplikace* `/Embedding`|Spuštění k úpravě vložené položky OLE.|  
|*Aplikace* `/Register`<br /><br /> *Aplikace* `/Regserver`|Informuje o aplikace k provádění úloh registrace.|  
|*Aplikace* `/Unregister`<br /><br /> *Aplikace* `/Unregserver`|Informuje o aplikace k provádění úloh zrušení registrace.|  
  
 Tyto informace jsou uloženy v [m_bRunAutomated](#m_brunautomated), [m_bRunEmbedded](#m_brunembedded), a [m_nShellCommand](#m_nshellcommand). Příznaky jsou označeny buď předat dál lomítko, **/**"nebo pomlčku" **-**'.  
  
 Výchozí implementace vloží do první parametr bez příznaku [m_strFileName](#m_strfilename). U `/pt` příznaku, výchozí implementace vloží druhý, třetí a čtvrtý bez příznaku parametry do [m_strPrinterName](#m_strprintername), [m_strDriverName](#m_strdrivername), a [m_ strPortName](#m_strportname), v uvedeném pořadí.  
  
 Výchozí implementace také nastaví [m_bShowSplash](#m_bshowsplash) k `TRUE` pouze v případě nový soubor. V případě nový soubor má uživatel prováděné akce, která zahrnuje vlastní aplikace. Ve všech ostatních případech, včetně otevření existující soubory pomocí prostředí akce uživatele zahrnuje soubor přímo. V hlediska zaměřené na dokument úvodní obrazovka nemusí oznamujeme spuštění aplikace.  
  
 Funkci ve vaší odvozené třídy za účelem zpracování jiných hodnot příznak a parametr přepište.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)   
 [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)

