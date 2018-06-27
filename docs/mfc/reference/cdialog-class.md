---
title: CDialog – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
dev_langs:
- C++
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ae7748c249cb9c7752b55d07bf10278c9c7f4ce
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955011"
---
# <a name="cdialog-class"></a>CDialog – třída
Základní třída používaná pro zobrazování dialogových oken na obrazovce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDialog : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDialog::CDialog](#cdialog)|Vytvoří `CDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDialog::Create](#create)|Inicializuje `CDialog` objektu. Dialogové okno nemodální vytvoří a připojí jej k `CDialog` objektu.|  
|[CDialog::CreateIndirect](#createindirect)|Vytvoří dialogové okno nemodální ze šablony dialogového v paměti (není založené na prostředcích).|  
|[CDialog::DoModal](#domodal)|Volá modální dialogové okno a vrátí po dokončení.|  
|[CDialog::EndDialog](#enddialog)|Modální dialogové okno se zavře.|  
|[CDialog::GetDefID](#getdefid)|Získá ID ovládacího prvku výchozí uzavření tlačítkem pro dialogové okno.|  
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|Přejdete k zadané dialogové ovládacího prvku v dialogovém okně.|  
|[CDialog::InitModalIndirect](#initmodalindirect)|Vytvoří modální dialogové okno ze šablony dialogového v paměti (není založené na prostředcích). Parametry jsou uloženy do funkce `DoModal` je volána.|  
|[CDialog::MapDialogRect](#mapdialogrect)|Dialogové okno-jednotky obdélníku převede na obrazovce jednotky.|  
|[CDialog::NextDlgCtrl](#nextdlgctrl)|Přejdete na další ovládací prvek dialogového v dialogovém okně.|  
|[CDialog::OnInitDialog](#oninitdialog)|Přepsání pro posílení inicializace – dialogové okno.|  
|[CDialog::OnSetFont](#onsetfont)|Přepsání určit písmo, které ovládacího prvku – dialogové okno se má používat při nakreslí text.|  
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|Přejdete do předchozího dialogového ovládacího prvku v dialogovém okně.|  
|[CDialog::SetDefID](#setdefid)|Zadaný pushbutton se změní výchozí uzavření tlačítkem ovládací prvek pro dialogové okno.|  
|[CDialog::SetHelpID](#sethelpid)|Nastaví ID Kontextová nápověda pro dialogové okno.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDialog::OnCancel](#oncancel)|Přepsání nastavení za účelem provedení tlačítko Zrušit nebo reakce na stisknutí klávesy ESC. Výchozí hodnota zavře dialogové okno a `DoModal` vrátí **IDCANCEL**.|  
|[CDialog::OnOK](#onok)|Přepsání nastavení za účelem provedení akce tlačítko OK v dialogovém okně modální. Výchozí hodnota zavře dialogové okno a `DoModal` vrátí **IDOK**.|  
  
## <a name="remarks"></a>Poznámky  
 Dialogová okna jsou dvou typů: modální a nemodální. Modální dialogové okno musejí být uzavřené uživatelem, než aplikace dál. Dialogové okno nemodální umožňuje uživatelům zobrazit dialogové okno a vrátíte se k jiné úlohy bez zrušení nebo odebrání dialogové okno.  
  
 A `CDialog` objektu je kombinací šablony dialogového okna a `CDialog`-odvozené třídy. Použití editoru dialogových oken k vytvoření šablony dialogové okno a uložte ho prostředek a potom pomocí průvodce Přidat třídu vytvořte třídy odvozené od `CDialog`.  
  
 Dialogového okna, jako je jiné okno přijímá zprávy ze systému Windows. V dialogovém okně jsou zvláště zájem o zpracování zpráv oznámení z ovládacích prvků dialogových oken, protože se jedná, jak se uživatel komunikuje s vašem dialogovém okně. Okno Vlastnosti použijte k výběru zprávy chcete pro popisovač a její přidá položky odpovídající mapy zpráv a obslužné rutiny zpráv členské funkce do třídy pro vás. Stačí pro zápis kódu pro konkrétní aplikace v členské funkce obslužné rutiny.  
  
 Pokud dáváte přednost, můžete vždy napsat položek mapy zpráv a členské funkce ručně.  
  
 Ve všech ale nejvíce trivial dialogových oken Přidat členské proměnné vlastní třídy odvozené dialogového okna pro ukládání dat v ovládacích prvcích dialogových oken zadaného uživatelem, nebo chcete-li zobrazit data pro uživatele. Můžete přidat proměnnou průvodce vytvořit členské proměnné a přidružit ovládací prvky. Ve stejnou dobu vyberte typ proměnné a povolený rozsah hodnot pro každou proměnnou. Kód průvodce přidá do vlastní třídy dialogového okna odvozené proměnné členů.  
  
 Mapování dat se generuje automaticky zpracovat výměnu dat mezi ovládacími prvky dialogových oken a proměnné členů. Mapování dat poskytuje funkce, které se inicializovat ovládací prvky v dialogovém okně s správné hodnoty, načtení dat a ověřit data.  
  
 Chcete-li modální dialogové okno vytvořit, vytvořit objekt v zásobníku pomocí konstruktoru pro vlastní třídy odvozené dialogového okna a potom volejte `DoModal` vytvoření dialogového okna a jeho ovládacích prvků. Pokud chcete vytvořit dialogového okna bez režimu, zavolejte `Create` v konstruktoru vlastní třídy dialogového okna.  
  
 Můžete také vytvořit šablonu v paměti pomocí [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) datové struktury, jak je popsáno v sadě Windows SDK. Po sestavení `CDialog` objektu, volání [CreateIndirect](#createindirect) k vytvoření nemodální dialogové okno nebo volání [InitModalIndirect](#initmodalindirect) a [DoModal](#domodal) vytvořit modální Dialogové okno.  
  
 Výměna a ověření mapování dat je napsána v přepsání `CWnd::DoDataExchange` přidaná do vaší nové třídy dialogového okna. Najdete v článku [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) – členská funkce v `CWnd` Další informace o funkci výměna a ověření.  
  
 Programátorů a volání framework `DoDataExchange` nepřímo prostřednictvím volání [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata).  
  
 Volání framework `UpdateData` když uživatel klikne na tlačítko OK a modální dialogové okno zavřete. (Není načtena data po kliknutí na tlačítko Storno.) Výchozí implementaci [OnInitDialog](#oninitdialog) také voláním `UpdateData` nastavit počáteční hodnoty ovládacích prvků. Obvykle přepsat `OnInitDialog` další inicializovat ovládací prvky. `OnInitDialog` je volána po vytvoření všech ovládacích prvků dialogové okno a těsně před dialogové okno se zobrazí pole.  
  
 Můžete volat `CWnd::UpdateData` kdykoli během provádění modální nebo nemodální dialogového okna.  
  
 Pokud vyvíjíte dialogového okna ručně, nezbytné členské proměnné přidejte do třídy odvozené dialogové sami a přidání členské funkce nastavit nebo získat tyto hodnoty.  
  
 Modální dialogové okno se automaticky zavře po stisknutí tlačítka OK nebo zrušit nebo když váš kód zavolá `EndDialog` – členská funkce.  
  
 Při implementaci dialogového okna bez režimu vždy přepsat `OnCancel` – členská funkce a volání `DestroyWindow` z v něm. Nemůžete volat základní třídy `CDialog::OnCancel`, protože zavolá `EndDialog`, který bude potlačit dialogové okno, ale se nezničí. Měli byste také přepsat `PostNcDestroy` pro nemodální dialogová okna, chcete-li odstranit **to**, protože nemodální dialogová okna jsou obvykle přiřazen **nové**. Modální dialogová okna se obvykle vytvářejí rámec a není nutné `PostNcDestroy` čištění.  
  
 Další informace o `CDialog`, najdete v části:  
  
- [Dialogová okna](../../mfc/dialog-boxes.md)  
  
-   Článek znalostní báze Knowledge Base Q262954: postupy: Vytvoření dialogového okna Resizeable s posuvníky  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cdialog"></a>  CDialog::CDialog  
 Můžete vytvořit na základě prostředků modální dialogové okno, volání buď veřejné formu konstruktoru.  
  
```  
explicit CDialog(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
explicit CDialog(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);  
  
CDialog();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszTemplateName*  
 Obsahuje řetězec ukončené hodnotou null, který je název prostředku šablony – dialogové okno.  
  
 *nIDTemplate*  
 Obsahuje počet ID prostředku šablony – dialogové okno.  
  
 *pParentWnd*  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je **NULL**, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Jednu formu konstruktor poskytuje přístup k prostředku dialogového okna podle názvu šablony. Další konstruktor poskytuje přístup podle čísla ID šablony, obvykle s **IDD_** předpona (například IDD_DIALOG1).  
  
 K vytvoření modální dialogové okno ze šablony v paměti, nejprve vyvolat konstruktor bez parametrů, chráněné a pak zavolají `InitModalIndirect`.  
  
 Poté, co vytvoříte modální dialogové okno s jedním z výše uvedených metod, volání `DoModal`.  
  
 Vytvoření nemodálního dialogové okno, používat chráněný formu `CDialog` konstruktor. Konstruktor je chráněna, protože musí být odvozeny vlastní dialogového třídu pro implementaci dialogového okna bez režimu. Vytváření nemodálních dialogového okna je dvoustupňový proces. První volání konstruktoru; potom zavolejte `Create` členskou funkci pro vytvoření založené na prostředcích dialogového okna, nebo volejte `CreateIndirect` dialogové okno Vytvořit ze šablony v paměti.  
  
##  <a name="create"></a>  CDialog::Create  
 Volání `Create` k vytvoření nemodálního okna pole použití šablony dialogového z prostředku.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
virtual BOOL Create(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszTemplateName*  
 Obsahuje řetězec ukončené hodnotou null, který je název prostředku šablony – dialogové okno.  
  
 *pParentWnd*  
 Odkazuje na nadřazený objekt okno (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je **NULL**, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.  
  
 *nIDTemplate*  
 Obsahuje počet ID prostředku šablony – dialogové okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nenulové hodnoty, pokud byly úspěšné; – dialogové okno Vytvoření a inicializace obou formulářů jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vložit volání `Create` v konstruktoru nebo volání po konstruktoru vyvolání.  
  
 Dvě formy `Create` – členská funkce jsou poskytovány pro přístup k prostředku šablony dialogového názvem šablony nebo šablony identifikační číslo (například IDD_DIALOG1).  
  
 Pro buď formulář předejte ukazatel okno nadřazený objekt. Pokud *pParentWnd* je **NULL**, vytvoří se dialogové okno s jeho nadřazený nebo vlastníka okno nastavena na hlavní okno aplikace.  
  
 `Create` – Členská funkce vrátí okamžitě po vytvoření dialogové okno.  
  
 Použití **ws_visible –** styl v šabloně – dialogové okno, pokud při vytváření nadřazené okno by se zobrazit dialogové okno. Jinak, musí volat `ShowWindow`. Další – dialogové okno Styly a jejich použití najdete v tématu [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktura ve Windows SDK a [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) v *odkaz knihovny MFC*.  
  
 Použití `CWnd::DestroyWindow` funkce zrušení dialogové okno vytvořené `Create` funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]  
  
##  <a name="createindirect"></a>  CDialog::CreateIndirect  
 Volání této funkce člen k nemodální dialogové okno Vytvořit ze šablony dialogového v paměti.  
  
```  
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDialogTemplate*  
 Odkazuje na paměti, která obsahuje šablonu dialogového použít k vytvoření dialogové okno. Tato šablona je ve formátu [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktura a řízení informace, jak je popsáno v sadě Windows SDK.  
  
 *pParentWnd*  
 Odkazuje na objekt okno nadřazeného objektu dialogového okna (typu [CWnd](../../mfc/reference/cwnd-class.md)). Pokud je **NULL**, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.  
  
 *lpDialogInit*  
 Odkazuje na **DLGINIT** prostředků.  
  
 *hDialogTemplate*  
 Obsahuje popisovač pro globální paměť obsahující šablonu – dialogové okno. Tato šablona je ve formátu **DLGTEMPLATE** strukturu a dat pro každý ovládací prvek v dialogovém okně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl vytvořen a úspěšná; inicializace dialogových oken jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `CreateIndirect` – Členská funkce vrátí okamžitě po vytvoření dialogové okno.  
  
 Použití **ws_visible –** styl v šabloně – dialogové okno, pokud při vytváření nadřazené okno by se zobrazit dialogové okno. Jinak, musí volat `ShowWindow` způsobí zobrazit. Další informace o tom, jak můžete zadat další styly dialogového v šabloně, najdete v článku [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktura ve Windows SDK.  
  
 Použití `CWnd::DestroyWindow` funkce zrušení dialogové okno vytvořené `CreateIndirect` funkce.  
  
 Dialogová okna, které obsahují ovládací prvky ActiveX vyžadovat další informace, které jsou součástí **DLGINIT** prostředků. Další informace najdete v článku znalostní báze Knowledge Base Q231591, "postupy: použití šablony dialogového okna vytvořit dialogové okno knihovny MFC s ovládacím prvkem ActiveX." Články znalostní báze jsou k dispozici na [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="domodal"></a>  CDialog::DoModal  
 Volání této funkce člen k vyvolání modálních dialogových oken a vrátí výsledek – dialogové okno po dokončení.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Int** hodnotu, která určuje hodnotu *Nvýsledek* parametr, který byl předán [CDialog::EndDialog](#enddialog) členská funkce, který se používá k dialogové okno zavřete. Vrácená hodnota je -1, pokud funkci nelze vytvořit dialogové okno, nebo **IDABORT** Pokud došlo k jiné chybě, v takovém případě ve výstupním okně bude obsahovat informace o chybě z [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen zpracovává veškerou interakci s uživatelem při dialogové okno je aktivní. To je díky modální; dialogových oken To znamená uživatel nemůže komunikovat s jinými dokud nezavře dialogové okno.  
  
 Pokud uživatel kliknutím na jednu z tlačítek v dialogovém okně, například OK nebo zrušit, členské funkce popisovač zpráv, jako například [onok –](#onok) nebo [oncancel –](#oncancel), nazývá se pokusit o dialogové okno zavřete. Výchozí hodnota `OnOK` – členská funkce budou ověření a aktualizovat data – dialogové okno a zavřete dialogové okno s tímto výsledkem **IDOK**a ve výchozím nastavení `OnCancel` – členská funkce se zavře dialogové okno s výsledek  **IDCANCEL** bez ověřování a aktualizace dat – dialogové okno. Tyto funkce obslužné rutiny zpráv změnit jejich chování můžete přepsat.  
  
> [!NOTE]
> `PreTranslateMessage` Nyní je volána pro zpracování zprávy modální dialogové okno pole.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]  
  
##  <a name="enddialog"></a>  CDialog::EndDialog  
 Volání této funkce člen ukončit modální dialogové okno.  
  
```  
void EndDialog(int nResult);
```  
  
### <a name="parameters"></a>Parametry  
 *Nvýsledek*  
 Obsahuje hodnotu, která má být vrácen z dialogového okna do volajícího `DoModal`.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu *Nvýsledek* jako návratová hodnota `DoModal`. Je nutné použít `EndDialog` funkci dokončí zpracování vždy, když je vytvořena modální dialogové okno.  
  
 Můžete volat `EndDialog` kdykoli, dokonce i v [OnInitDialog](#oninitdialog), v takovém případě by měl zavřete dialogové okno dříve, než se zobrazí nebo před nastavením zaměření pro vstup.  
  
 `EndDialog` okamžitě nezavře dialogové okno. Místo toho nastaví příznak, který přesměruje dialogové okno zavřete, jakmile vrátí aktuální popisovač zpráv.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]  
  
##  <a name="getdefid"></a>  CDialog::GetDefID  
 Volání `GetDefID` – členská funkce získat ID ovládacího prvku výchozí uzavření tlačítkem pro dialogové okno.  
  
```  
DWORD GetDefID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu 32-bit ( `DWORD`). Pokud výchozí pushbutton má hodnotu ID, obsahuje slovo horní **DC_HASDEFID** a word nejnižší hodnotu ID. Pokud výchozí pushbutton nemá hodnotu ID, je vrácenou hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Je to obvykle tlačítko OK.  
  
##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl  
 Přejdete k daný ovládací prvek v dialogovém okně.  
  
```  
void GotoDlgCtrl(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndCtrl*  
 Identifikuje okna (řízení), které má být vybrán.  
  
### <a name="remarks"></a>Poznámky  
 Získání ukazatele na ovládací prvek (podřízeného okna) předat jako *pWndCtrl*, volání `CWnd::GetDlgItem` členská funkce, která vrátí hodnotu ukazatel na [CWnd](../../mfc/reference/cwnd-class.md) objektu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem).  
  
##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect  
 Volání této funkce člen inicializovat objekt modálních dialogových pomocí šablony – dialogové okno, které vytvoříte v paměti.  
  
```  
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDialogTemplate*  
 Odkazuje na paměti, která obsahuje šablonu dialogového použít k vytvoření dialogové okno. Tato šablona je ve formátu [DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394) struktura a řízení informace, jak je popsáno v sadě Windows SDK.  
  
 *hDialogTemplate*  
 Obsahuje popisovač pro globální paměť obsahující šablonu – dialogové okno. Tato šablona je ve formátu **DLGTEMPLATE** strukturu a dat pro každý ovládací prvek v dialogovém okně.  
  
 *pParentWnd*  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je **NULL**, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.  
  
 *lpDialogInit*  
 Odkazuje na **DLGINIT** prostředků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl vytvořen a inicializován úspěšně; objektu dialogového okna jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li modální dialogové okno Vytvořit nepřímo, nejprve přidělit blok globální paměti a vyplnit pole šablony dialogového okna. Potom zavolejte prázdné `CDialog` konstruktor k vytvoření objektu – dialogové okno. Pak zavolejte `InitModalIndirect` k uložení vaší popisovač šablony v paměti – dialogové okno. Dialogové okno se vytvoří a zobrazí novější, pokud [DoModal](#domodal) členské funkce je volána.  
  
 Dialogová okna, které obsahují ovládací prvky ActiveX vyžadovat další informace, které jsou součástí **DLGINIT** prostředků. Další informace najdete v článku znalostní báze Knowledge Base Q231591, "postupy: použití šablony dialogového okna vytvořit dialogové okno knihovny MFC s ovládacím prvkem ActiveX." Články znalostní báze jsou k dispozici na [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect  
 Chcete-li převést – dialogové okno jednotky obdélníku na obrazovce jednotky volání.  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprect –*  
 Odkazuje na [Rect –](../../mfc/reference/rect-structure1.md) struktura nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje – dialogové okno koordinuje má být převeden.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno-jednotky jsou vyjádřený jako aktuální základní jednotku – dialogové okno odvozené od průměrná šířka a výška znaků písmo použité pro – dialogové okno text. Jednu jednotku vodorovné je jeden čtvrtý jednotky základní šířkou – dialogové okno a jednu jednotku svislé osmina jednotky základní výška – dialogové okno.  
  
 **GetDialogBaseUnits** funkce Windows vrací informace o velikosti písma systému, ale jiné písmo pro každé pole v dialogovém okně můžete zadat, pokud použijete **DS_SETFONT** styl v Soubor definice prostředků. `MapDialogRect` Funkce systému Windows používá příslušného písma pro tohoto dialogového okna.  
  
 `MapDialogRect` – Členská funkce nahrazuje dialogového jednotky v *lprect –* s obrazovky jednotek (v pixelech) tak, aby rámeček umožňuje vytvoření dialogového nebo umístit ovládacího prvku v rámci pole.  
  
##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl  
 Přejdete na další ovládací prvek v dialogovém okně.  
  
```  
void NextDlgCtrl() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je zaměření na poslední ovládacího prvku v dialogovém okně, přesune ho do ovládacího prvku první.  
  
##  <a name="oncancel"></a>  CDialog::OnCancel  
 Rozhraní framework volá tuto metodu, když uživatel klikne **zrušit** nebo stisknutí klávesy ESC v modální nebo nemodálním dialogovém okně.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro provádění akcí (například obnovení stará data) když uživatel zavře dialogové okno kliknutím **zrušit** nebo stisknutí klávesy ESC. Výchozí hodnota zavře modální dialogové okno voláním [EndDialog](#enddialog) a způsobit tak [DoModal](#domodal) vrátit IDCANCEL.  
  
 Pokud implementujete **zrušit** tlačítko v nemodálním dialogovém okně, je nutné přepsat `OnCancel` metoda a volání [destroywindow –](../../mfc/reference/cwnd-class.md#destroywindow) uvnitř ho. Nevolejte metodu základní třídy, protože zavolá `EndDialog`, který bude potlačit dialogové okno, ale není zničte jej.  
  
> [!NOTE]
>  Nelze přepsat tuto metodu použijete `CFileDialog` objektu v programu, který je přeložen v systému Windows XP. Další informace o `CFileDialog`, najdete v části [CFileDialog třída](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]  
  
##  <a name="oninitdialog"></a>  CDialog::OnInitDialog  
 Tato metoda je volána v reakci `WM_INITDIALOG` zprávy.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje, zda má být z aplikace nastavte na některou z ovládacích prvků zaměření pro vstup v dialogovém okně. Pokud `OnInitDialog` vrátí nenulovou, Windows nastaví zaměření pro vstup do výchozího umístění, první prvek v dialogovém okně. Aplikace může vrátit 0, pouze v případě, že se má explicitně nastavit zaměření pro vstup na jednu z ovládacích prvků v dialogovém okně.  
  
### <a name="remarks"></a>Poznámky  
 Systém Windows odešle `WM_INITDIALOG` zpráva do dialogového okna během [vytvořit](#create), [CreateIndirect](#createindirect), nebo [DoModal](#domodal) volání, které nastat bezprostředně před dialogových oken Zobrazí se.  
  
 Potlačí tuto metodu, pokud chcete provést zvláštní zpracování při inicializaci dialogové okno. V přepsané verze, nejprve volat základní třídy `OnInitDialog` však Ignorovat hodnoty. Obvykle bude vracet `TRUE` z přepsaného metodu.  
  
 Volání Windows `OnInitDialog` funkce pomocí běžných standardní globální – dialogové okno postupu do všech Microsoft Foundation Class Library dialogových oken. Nevyvolá tuto funkci prostřednictvím vaší mapy zpráv, a proto není nutné položku mapy zpráv pro tuto metodu.  
  
> [!NOTE]
> Nelze přepsat tuto metodu použijete `CFileDialog` objektu v programu, který je přeložen v systému Windows Vista nebo novější operační systémy. Další informace o změnách `CFileDialog` v systému Windows Vista a novější, najdete v části [CFileDialog třída](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]  
  
##  <a name="onok"></a>  CDialog::OnOK  
 Volá se, když uživatel klikne **OK** (tlačítko s ID IDOK).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu pro provádění akcí při **OK** se aktivuje tlačítko. Pokud se dialogové okno obsahuje ověřování automatické dat a serveru exchange, výchozí implementace této metody ověří data dialogového okna a aktualizuje příslušné proměnné ve vaší aplikaci.  
  
 Pokud implementujete **OK** tlačítko v nemodálním dialogovém okně, je nutné přepsat `OnOK` metoda a volání [destroywindow –](../../mfc/reference/cwnd-class.md#destroywindow) uvnitř ho. Nevolejte metodu základní třídy, protože zavolá [EndDialog](#enddialog) který dialogové okno neviditelná se ale nezničí ho.  
  
> [!NOTE]
>  Nelze přepsat tuto metodu použijete `CFileDialog` objektu v programu, který je přeložen v systému Windows XP. Další informace o `CFileDialog`, najdete v části [CFileDialog třída](../../mfc/reference/cfiledialog-class.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]  
  
##  <a name="onsetfont"></a>  CDialog::OnSetFont  
 Určuje písmo, které ovládacího prvku – dialogové okno bude používat při kreslení textu.  
  
```  
Virtual void OnSetFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pFont*  
 Určuje ukazatel na písma, který se použije jako výchozí pro všechny ovládací prvky v tomto seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno použije zadanou písmo jako výchozí pro všechny její ovládací prvky.  
  
 Písmo – dialogové okno editoru dialogových oken obvykle nastaví jako součást prostředek – dialogové okno šablony.  
  
> [!NOTE]
> Nelze přepsat tuto metodu použijete `CFileDialog` objektu v programu, který je přeložen v systému Windows Vista nebo novější operační systémy. Další informace o změnách `CFileDialog` v systému Windows Vista a novější, najdete v části [CFileDialog třída](../../mfc/reference/cfiledialog-class.md).  
  
##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl  
 Nastaví fokus na předchozí ovládacího prvku v dialogovém okně.  
  
```  
void PrevDlgCtrl() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je zaměření na první prvek v dialogovém okně, jeho přejde na poslední ovládací prvek v poli.  
  
##  <a name="setdefid"></a>  CDialog::SetDefID  
 Změní výchozí uzavření tlačítkem ovládací prvek pro dialogové okno.  
  
```  
void SetDefID(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *nID*  
 Určuje ID uzavření tlačítkem ovládací prvek, který se stane výchozí.  
  
##  <a name="sethelpid"></a>  CDialog::SetHelpID  
 Nastaví ID Kontextová nápověda pro dialogové okno.  
  
```  
void SetHelpID(UINT nIDR);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDR*  
 Určuje ID kontextové nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka DLGCBR32 MFC](../../visual-cpp-samples.md)   
 [Ukázka MFC DLGTEMPL](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

