---
title: CPropertyPage – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
dev_langs:
- C++
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 632e8c0039dc0cac35fe46cff1fc539e534f8e20
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757507"
---
# <a name="cpropertypage-class"></a>CPropertyPage – třída
Představuje jednotlivé stránky seznamu vlastností, jinak známé jako dialogové okno Karta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPropertyPage : public CDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropertyPage::CPropertyPage](#cpropertypage)|Vytvoří `CPropertyPage` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropertyPage::CancelToClose](#canceltoclose)|Změní na tlačítko OK číst zavřít a zakáže tlačítko Storno po neopravitelné změnit na stránce modální seznam vlastností.|  
|[CPropertyPage::Construct](#construct)|Vytvoří `CPropertyPage` objektu. Použití `Construct` Pokud chcete zadat parametry v době běhu, nebo pokud používáte pole.|  
|[CPropertyPage::GetPSP](#getpsp)|Načte Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) struktura `CPropertyPage` objektu.|  
|[CPropertyPage::OnApply](#onapply)|Volá se rozhraním, když dojde ke kliknutí na tlačítko použít.|  
|[CPropertyPage::OnCancel](#oncancel)|Volá se rozhraním, když dojde ke kliknutí na tlačítko Storno.|  
|[CPropertyPage::OnKillActive](#onkillactive)|Volá se rozhraním, když aktuální stránka už není aktivní stránkou. Ověřování dat v tomto poli.|  
|[CPropertyPage::OnOK](#onok)|Volá se rozhraním, když je kliknutí OK, použít nebo zavřít.|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Volá se rozhraním, když dojde ke kliknutí na tlačítko Storno a před místo zrušení.|  
|[CPropertyPage::OnReset](#onreset)|Volá se rozhraním, když dojde ke kliknutí na tlačítko Storno.|  
|[CPropertyPage::OnSetActive](#onsetactive)|Volá se rozhraním, když se stránka stane aktivní stránkou.|  
|[CPropertyPage::OnWizardBack](#onwizardback)|Volá se rozhraním při kliknutí na tlačítko zpět při používání seznamu vlastností wizard-type.|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Volá se rozhraním, když je kliknutí na tlačítko Dokončit při používání seznamu vlastností wizard-type.|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|Volá se rozhraním při kliknutí na tlačítko Další při používání seznamu vlastností wizard-type.|  
|[CPropertyPage::QuerySiblings](#querysiblings)|Předá zprávu na každou stránku vlastností.|  
|[CPropertyPage::SetModified](#setmodified)|Volání za účelem aktivace nebo deaktivace tlačítko použít.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) struktury. Poskytuje přístup k základní vlastnost parametry stránky.|  
  
## <a name="remarks"></a>Poznámky  
 Jak se standardní dialogová okna, odvoďte třídu z `CPropertyPage` pro každou stránku vašeho seznamu vlastností. Použití `CPropertyPage`-nejprve vytvořit odvozené objekty [cpropertysheet –](../../mfc/reference/cpropertysheet-class.md) objektu a pak vytvořte objekt pro každou stránku, který odkazuje v seznamu vlastností. Volání [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) pro každou stránku v seznamu a zobrazte seznam vlastností voláním [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) pro modální seznam vlastností, nebo [cpropertysheet –:: Vytvoření](../../mfc/reference/cpropertysheet-class.md#create) pro nemodálního seznamu vlastností.  
  
 Můžete vytvořit typ dialogové okno Karta nazývá průvodce, který se skládá z seznam vlastností s posloupnost stránky vlastností, které provedou uživatele kroky operace, jako je například nastavení zařízení nebo vytváření bulletinu. V dialogovém okně wizard-type. karta na stránkách vlastností nemají karty a pouze jednu vlastnost stránka není viditelná v čase. Namísto toho tlačítka OK a použít dialogové okno Karta wizard-type. má také tlačítko Zpět, tlačítko Další nebo Dokončit a tlačítko Storno.  
  
 Další informace o vytvoření seznamu vlastností jako průvodce najdete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Další informace o používání `CPropertyPage` objekty, najdete v článku [seznamy vlastností a stránky vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose  
 Voláním této funkce po provedení neopravitelné změny dat na stránce modální seznam vlastností.  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se změnit na tlačítko OK zavřete a zakázat tlačítko Storno. Tato změna upozornění, která uživatele, že změna je trvalé a změny se nedá zrušit.  
  
 `CancelToClose` Členská funkce neprovede v nemodálního seznamu vlastností, protože nemodálního seznamu vlastností nemá žádné tlačítko Storno ve výchozím nastavení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::QuerySiblings](#querysiblings).  
  
##  <a name="construct"></a>  CPropertyPage::Construct  
 Voláním této členské funkce k vytvoření `CPropertyPage` objektu.  
  
```  
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0);

 
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDTemplate*  
 ID šablony použité pro tuto stránku.  
  
 *nIDCaption*  
 ID názvu umístit na kartě pro tuto stránku. Pokud je 0, název se provedou v šabloně dialogu pro tuto stránku.  
  
 *lpszTemplateName*  
 Obsahuje řetězec zakončený hodnotou null, který je název prostředku šablony.  
  
 *nIDHeaderTitle*  
 ID názvu budou umístěny v umístění názvu vlastnosti záhlaví stránky. Ve výchozím nastavení 0.  
  
 *nIDHeaderSubTitle*  
 ID názvu budou umístěny v umístění podnadpis vlastnosti záhlaví stránky. Ve výchozím nastavení 0.  
  
### <a name="remarks"></a>Poznámky  
 Objekt se zobrazí, jakmile jsou splněny všechny následující podmínky:  
  
-   Na stránce byl přidán do listu vlastností pomocí [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Seznam vlastností [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [vytvořit](../../mfc/reference/cpropertysheet-class.md#create) byla volána funkce.  
  
-   Uživatel vybral (s kartami k) na této stránce.  
  
 Volání `Construct` Pokud jeden z jiné třídy konstruktory se nevolala. `Construct` Členská funkce je flexibilní, protože můžete nechat prázdné parametr příkazu a pak zadejte více parametrů a konstrukce v libovolném bodě v kódu.  
  
 Je nutné použít `Construct` při práci s poli, a je nutné volat `Construct` pro každého člena pole tak, aby datové členy jsou přiřazeny odpovídajícími hodnotami.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]  
  
##  <a name="cpropertypage"></a>  CPropertyPage::CPropertyPage  
 Vytvoří `CPropertyPage` objektu.  
  
```  
CPropertyPage();

 
explicit CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
explicit CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```  
  
### <a name="parameters"></a>Parametry  
 *nIDTemplate*  
 ID šablony použité pro tuto stránku.  
  
 *nIDCaption*  
 ID názvu umístit na kartě pro tuto stránku. Pokud je 0, název se provedou v šabloně dialogu pro tuto stránku.  
  
 *dwSize*  
 *lpszTemplateName*  
 Odkazuje na řetězec obsahující název šablony pro tuto stránku. Nemůže mít hodnotu NULL.  
  
 *nIDHeaderTitle*  
 ID názvu budou umístěny v umístění názvu vlastnosti záhlaví stránky.  
  
 *nIDHeaderSubTitle*  
 ID názvu budou umístěny v umístění podnadpis vlastnosti záhlaví stránky.  
  
### <a name="remarks"></a>Poznámky  
 Objekt se zobrazí, jakmile jsou splněny všechny následující podmínky:  
  
-   Na stránce byl přidán do listu vlastností pomocí [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Seznam vlastností [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [vytvořit](../../mfc/reference/cpropertysheet-class.md#create) byla volána funkce.  
  
-   Uživatel vybral (s kartami k) na této stránce.  
  
 Pokud máte více parametrů (například, pokud používáte pole), použijte [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) místo `CPropertyPage`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="getpsp"></a>  CPropertyPage::GetPSP  
 Načte Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) struktura `CPropertyPage` objektu.  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `PROPSHEETPAGE` struktury.  
  
##  <a name="m_psp"></a>  CPropertyPage::m_psp  
 `m_psp` je struktura, jejíž členové uložení vlastnosti [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2).  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tuto strukturu použijte pro inicializaci vzhled stránky vlastností po jejím vytváření.  
  
 Další informace o této struktuře, včetně seznamu členů, naleznete v tématu `PROPSHEETPAGE` v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="onapply"></a>  CPropertyPage::OnApply  
 Tato členská funkce je voláno rozhraním, když se uživatel rozhodne OK nebo tlačítko použít.  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud jsou změny přijaty; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Když tuto funkci volá rozhraní framework, přijímají se změny provedené na všechny stránky vlastností v okně vlastností, seznamu vlastností zachová fokus, a `OnApply` vrátí hodnotu TRUE (hodnota 1). Před `OnApply` může být volána rozhraním, musíte zavoláte [SetModified](#setmodified) a nastavte její parametr na hodnotu TRUE. Aktivuje toto tlačítko použít. poté, co uživatel provede změny na stránce vlastností.  
  
 Přepsání této členské funkce lze určit, jakou akci program provede, když uživatel klikne na tlačítko použít. Při přepsání, funkce by měla vrátit TRUE, pokud chcete přijmout změny a hodnotu FALSE a znemožnit změny tak vliv.  
  
 Výchozí implementace `OnApply` volání `OnOK`.  
  
 Další informace o oznámení poslaných zpráv, když uživatel stiskne použít na tlačítko OK v okně vlastností najdete v tématu [PSN_APPLY](/windows/desktop/Controls/psn-apply) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::OnOK](#onok).  
  
##  <a name="oncancel"></a>  CPropertyPage::OnCancel  
 Tato členská funkce je voláno rozhraním při výběru tlačítka Storno.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Poznámky  
 Přepište tato členská funkce k provedení akce pro tlačítko Storno. Výchozí nastavení Neguje změnách, které byly provedeny.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive  
 Tato členská funkce je voláno rozhraním, když stránku už není aktivní stránkou.  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud data se aktualizují úspěšně, jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce k provádění úloh ověření speciální datové přepište.  
  
 Výchozí implementace tato členská funkce zkopíruje nastavení z ovládacích prvků na stránce vlastností do členské proměnné stránky vlastností. Pokud data nebyla úspěšně aktualizována z důvodu chyby ověření (DDV) dat dialogového okna, stránky zachová fokus.  
  
 Až tato členská funkce vrátí úspěšně, zavolá rozhraní na stránce [onok –](#onok) funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="onok"></a>  CPropertyPage::OnOK  
 Tato členská funkce se volá se rozhraním, když se uživatel rozhodne OK nebo použít tlačítko ihned po volání rozhraní framework [onkillactive –](#onkillactive).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Poznámky  
 Když se uživatel rozhodne OK nebo použít tlačítko, rozhraní přijímá [PSN_APPLY](/windows/desktop/Controls/psn-apply) oznámení na stránce vlastností. Volání `OnOK` nebudou provedeny při volání [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) vzhledem k tomu, že na stránce vlastností neodešle oznámení v takovém případě.  
  
 Přepište tato členská funkce implementovat další chování specifické pro aktuálně aktivní stránkou. když uživatel nezavře celý seznam vlastností.  
  
 Výchozí implementace tato členská funkce, označení stránky jako "clean" tak, aby odrážely, že data se aktualizují v `OnKillActive` funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel  
 Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Storno a před zrušení akce proběhla.  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu FALSE, aby se zabránilo operace zrušení nebo TRUE, pokud chcete povolit.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této členské funkce lze určit akci, kterou program provede, když uživatel klikne na tlačítko Storno.  
  
 Výchozí implementace `OnQueryCancel` vrátí hodnotu TRUE.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="onreset"></a>  CPropertyPage::OnReset  
 Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Storno.  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>Poznámky  
 Když tuto funkci volá rozhraní framework, pro všechny stránky vlastností, které byly provedené uživatelem dříve kliknutím na tlačítko použít změny se zahodí a seznam vlastností uchovává fokus.  
  
 Přepsání této členské funkce lze určit, jakou akci provede program, když uživatel klikne na tlačítko Storno.  
  
 Výchozí implementace `OnReset` nemá žádný účinek.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::OnCancel](#oncancel).  
  
##  <a name="onsetactive"></a>  CPropertyPage::OnSetActive  
 Tato členská funkce je voláno rozhraním při stránky je vybrán uživatelem a stane aktivní stránkou.  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud na stránce se úspěšně nastavila aktivní; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přepište tato členská funkce k provádění úloh, když je aktivován na stránce. Přepsání metody tato členská funkce by obvykle volání výchozí verze po aktualizaci datové členy, aby mělo aktualizovat stránku ovládací prvky s novými daty.  
  
 Výchozí implementace vytvoří okno pro stránku, není-li dřív vytvořili a díky tomu aktivní stránkou.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).  
  
##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack  
 Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Zpět v průvodci.  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 0 na automatický přechod na další stránku. na stránce zabránit ve změně hodnotu -1. Přejít na stránku, než na kterém další vrátíte identifikátor zobrazení dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této členské funkce lze zadat některá z akcí, které musí uživatel provést, když se stiskne tlačítko Zpět.  
  
 Další informace o tom, aby seznamu vlastností wizard-type, naleznete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish  
 Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Dokončit v průvodci.  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud seznam vlastností je zničen při dokončení Průvodce; jinak nula.  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel klikne **Dokončit** tlačítko v průvodci, rozhraní volá tuto funkci, kdy `OnWizardFinish` vrátí hodnotu TRUE (nenulovou hodnotu), seznam vlastností je možné, který se má zničit (ale není ve skutečnosti zničen). Volání `DestroyWindow` zničit okno vlastností. Nevolejte `DestroyWindow` z `OnWizardFinish`; to uděláte tak způsobí poškození haldy nebo jiné chyby.  
  
 Můžete přepsat tato členská funkce k určení některá z akcí, které musí uživatel provést, když se stiskne tlačítko Dokončit. Při přepisování tuto funkci, vrátí hodnotu FALSE, aby seznam vlastností z zničen.  
  
 Další informace o oznámení poslaných zpráv, když uživatel stiskne tlačítko pro dokončení v seznamu vlastností průvodce najdete v tématu [PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) v sadě Windows SDK.  
  
 Další informace o tom, aby seznamu vlastností wizard-type, naleznete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext  
 Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Další v průvodci.  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 0 na automatický přechod na další stránku. na stránce zabránit ve změně hodnotu -1. Přejít na stránku, než na kterém další vrátíte identifikátor zobrazení dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této členské funkce lze zadat některá z akcí, které musí uživatel provést, když se stiskne tlačítko Další.  
  
 Další informace o tom, aby seznamu vlastností wizard-type, naleznete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]  
  
##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings  
 Voláním této členské funkce pro předávání zpráv na každou stránku v seznamu vlastností.  
  
```  
LRESULT QuerySiblings(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 *wParam*  
 Určuje další informace, závislé na zprávu.  
  
 *lParam*  
 Určuje další informace, závislé na zprávu  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu ze stránky seznamu vlastností, nebo 0, pokud všechny stránky vrátit hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud na stránce vrátí nenulovou hodnotu, seznam vlastností neodešle zprávy na následujících stránkách.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="setmodified"></a>  CPropertyPage::SetModified  
 Zavolejte tuto členskou funkci chcete povolit nebo zakázat tlačítko použít, založené na tom, zda bude použito nastavení na stránce vlastností pro příslušný objekt externí.  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bChanged*  
 Hodnota TRUE označuje, že nastavení stránky vlastností byl změněn od posledního se uplatňují; FALSE označuje, že nastavení stránky vlastností se použily, nebo třeba ji ignorovat.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework udržuje sledování, které stránky jsou "nečisté", to znamená, u kterých jste volali stránky vlastností `SetModified( TRUE )`. Tlačítko použít. bude vždy povolen při volání `SetModified( TRUE )` pro jednu ze stránek. Tlačítko použít. bude zakázáno, při volání `SetModified( FALSE )` pro jednu ze stránek, ale pouze pokud žádná z ostatních stránek není "dirty."  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL1 knihovny MFC](../../visual-cpp-samples.md)   
 [Ukázka CMNCTRL2 knihovny MFC](../../visual-cpp-samples.md)   
 [Ukázky knihovny MFC PROPDLG](../../visual-cpp-samples.md)   
 [Ukázky knihovny MFC SNAPVW](../../visual-cpp-samples.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cpropertysheet – třída](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
