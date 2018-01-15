---
title: "CPropertyPage – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c42a0ba40797312a2108a288fecdea55c6873f3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cpropertypage-class"></a>CPropertyPage – třída
Představuje jednotlivých stránek vlastností známé jako dialogové okno karty.  
  
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
|[CPropertyPage::CancelToClose](#canceltoclose)|Změní na tlačítko OK číst zavřít a zakáže tlačítko Zrušit po neopravitelné změnu v hodnotě stránce modální vlastností.|  
|[CPropertyPage::Construct](#construct)|Vytvoří `CPropertyPage` objektu. Použití `Construct` Pokud chcete zadat parametry v době běhu, nebo pokud používáte pole.|  
|[CPropertyPage::GetPSP](#getpsp)|Načte Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) struktura přidružené `CPropertyPage` objektu.|  
|[CPropertyPage::OnApply](#onapply)|Voláno rámcem při kliknutí na tlačítko použít.|  
|[CPropertyPage::OnCancel](#oncancel)|Voláno rámcem při kliknutí na tlačítko Storno.|  
|[CPropertyPage::OnKillActive](#onkillactive)|Voláno rámcem, pokud aktuální stránku už není aktivní stránky. Ověřování dat v tomto poli.|  
|[CPropertyPage::OnOK](#onok)|Voláno rámcem při kliknutí na OK, teď použít na tlačítko Zavřít.|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Voláno rámcem při kliknutí na tlačítko Storno, a před neproběhla Storno.|  
|[CPropertyPage::OnReset](#onreset)|Voláno rámcem při kliknutí na tlačítko Storno.|  
|[CPropertyPage::OnSetActive](#onsetactive)|Voláno rámcem při stránky active stránky.|  
|[CPropertyPage::OnWizardBack](#onwizardback)|Voláno rámcem při kliknutí na tlačítko Zpět na při použití Průvodce typu vlastností.|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Voláno rámcem při kliknutí na tlačítko Dokončit při použití Průvodce typu vlastností.|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|Voláno rámcem při kliknutí na tlačítko Další při použití Průvodce typu vlastností.|  
|[CPropertyPage::QuerySiblings](#querysiblings)|Předá zprávu na každou stránku vlastností.|  
|[CPropertyPage::SetModified](#setmodified)|Volání aktivovat nebo deaktivovat tlačítko použít.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) struktury. Poskytuje přístup k základní vlastnost parametry stránky.|  
  
## <a name="remarks"></a>Poznámky  
 Jako standardní dialogová okna, odvození třídy z `CPropertyPage` pro jednotlivé stránky ve vašem seznamu vlastností. Použít `CPropertyPage`-odvozené objekty, nejprve vytvořit [cpropertysheet –](../../mfc/reference/cpropertysheet-class.md) objektu a pak vytvořte objekt pro jednotlivé stránky, která je uložena do seznamu vlastností. Volání [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) pro všechny stránky v listu a zobrazte seznam vlastností voláním [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) pro modální vlastností, nebo [cpropertysheet –:: Vytvoření](../../mfc/reference/cpropertysheet-class.md#create) pro nemodálního seznamu vlastností.  
  
 Můžete vytvořit typ dialogového okna Karta nazývá průvodce, který se skládá z vlastností s posloupností stránky vlastností, které průvodce provede kroky pro operace, jako je například nastavení zařízení nebo vytváření bulletinu uživatele. V dialogovém okně Karta Průvodce type stránek vlastností nemají karty a současně je viditelná pouze jednu vlastnost stránky. Místo nutnosti tlačítka OK a použít nyní, dialogové okno Průvodce typu karta má také tlačítko Zpět, tlačítko Další nebo Dokončit a tlačítko Zrušit.  
  
 Další informace o vytvoření seznamu vlastností jako průvodce najdete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Další informace o používání `CPropertyPage` objekty, najdete v článku [vlastností a stránky vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="canceltoclose"></a>CPropertyPage::CancelToClose  
 Po neopravitelné změn dat na stránce vlastností modální volání této funkce.  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce bude změňte na tlačítko OK ukončete a zakažte na tlačítko Storno. Tato změna výstrahy, které uživatele, že je změna trvalé a změny nelze zrušit.  
  
 `CancelToClose` – Členská funkce se nic nestane. v nemodálního seznamu vlastností, protože nemodálního seznamu vlastností nemá ve výchozím nastavení tlačítko Zrušit.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::QuerySiblings](#querysiblings).  
  
##  <a name="construct"></a>CPropertyPage::Construct  
 Volání této funkce člen k vytvoření `CPropertyPage` objektu.  
  
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
 `nIDTemplate`  
 ID šablony použité pro tuto stránku.  
  
 `nIDCaption`  
 ID názvu se mají umístit na kartě pro tuto stránku. Pokud 0, bude název převzat ze šablony dialogového okna pro tuto stránku.  
  
 `lpszTemplateName`  
 Obsahuje řetězec ukončené hodnotou null, který je název prostředku šablony.  
  
 `nIDHeaderTitle`  
 ID názvu umístit do umístění název vlastnosti záhlaví stránky. Ve výchozím nastavení 0.  
  
 `nIDHeaderSubTitle`  
 ID názvu umístit do umístění subtitle vlastnosti záhlaví stránky. Ve výchozím nastavení 0.  
  
### <a name="remarks"></a>Poznámky  
 Objekt se zobrazí, jakmile jsou splněny všechny následující podmínky:  
  
-   Stránky byl přidán do listu vlastností pomocí [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Seznam vlastností [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [vytvořit](../../mfc/reference/cpropertysheet-class.md#create) funkce byla volána.  
  
-   Uživatel vybral (na kartách k) na této stránce.  
  
 Volání **vytvořit** Pokud jeden z jiné třídy konstruktorů nebyla volána. `Construct` – Členská funkce je flexibilní, protože můžete ponechat prázdné příkaz parametr a potom zadejte více parametrů a konstrukce v libovolném bodě v kódu.  
  
 Je nutné použít `Construct` při práci s pole a musí volat **vytvořit** pro každého člena pole tak, aby členové data jsou přiřazeny správné hodnoty.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]  
  
##  <a name="cpropertypage"></a>CPropertyPage::CPropertyPage  
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
 `nIDTemplate`  
 ID šablony použité pro tuto stránku.  
  
 `nIDCaption`  
 ID názvu se mají umístit na kartě pro tuto stránku. Pokud 0, bude název převzat ze šablony dialogového okna pro tuto stránku.  
  
 `dwSize`  
 `lpszTemplateName`  
 Odkazuje na řetězec obsahující název šablony pro tuto stránku. Nemůže být **NULL**.  
  
 `nIDHeaderTitle`  
 ID názvu umístit do umístění název vlastnosti záhlaví stránky.  
  
 `nIDHeaderSubTitle`  
 ID názvu umístit do umístění subtitle vlastnosti záhlaví stránky.  
  
### <a name="remarks"></a>Poznámky  
 Objekt se zobrazí, jakmile jsou splněny všechny následující podmínky:  
  
-   Stránky byl přidán do listu vlastností pomocí [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).  
  
-   Seznam vlastností [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [vytvořit](../../mfc/reference/cpropertysheet-class.md#create) funkce byla volána.  
  
-   Uživatel vybral (na kartách k) na této stránce.  
  
 Pokud máte několik parametrů (například pokud používáte pole), použijte [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) místo `CPropertyPage`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="getpsp"></a>CPropertyPage::GetPSP  
 Načte Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) struktura přidružené `CPropertyPage` objektu.  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na **PROPSHEETPAGE** struktury.  
  
##  <a name="m_psp"></a>CPropertyPage::m_psp  
 `m_psp`je struktura, jejíž členové uložení charakteristika [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548).  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato struktura použijte k chybě při inicializaci vzhled stránky vlastností po je vytvořený.  
  
 Další informace o tuto strukturu, včetně seznamu svých členů, najdete v části **PROPSHEETPAGE** ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="onapply"></a>CPropertyPage::OnApply  
 Tento člen funkce je volána rámcem, když uživatel vybere OK nebo tlačítko použít.  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou přijata změny; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Když tato funkce volá framework, jsou podmínky přijaty změny provedené na všechny stránky vlastností v seznamu vlastností, seznamu vlastností zachová fokus, a `OnApply` vrátí **TRUE** (hodnota 1). Před `OnApply` lze volat ve rozhraní, můžete musí mít název [SetModified](#setmodified) a nastavit jeho parametr na **TRUE**. Jakmile uživatel provede změny na stránce vlastností to bude aktivovat tlačítko použít.  
  
 Chcete-li určit, jakou akci váš program provede, když uživatel klikne na tlačítko použít funkci člena přepište. Při přepsání, by měla vrátit funkce **TRUE** kvůli přijetí změn a **FALSE** zabránit změny neprojeví.  
  
 Výchozí implementaci `OnApply` volání `OnOK`.  
  
 Další informace o zprávy oznámení po stisknutí použít nyní na tlačítko OK v seznamu vlastností najdete v tématu [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::OnOK](#onok).  
  
##  <a name="oncancel"></a>CPropertyPage::OnCancel  
 Tento člen funkce je volána rámcem, pokud je vybrána na tlačítko Storno.  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci k provádění akcí tlačítka Storno přepište. Výchozí hodnota Neguje veškeré změny, které byly provedeny.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="onkillactive"></a>CPropertyPage::OnKillActive  
 Tento člen funkce je volána rámcem když stránku už není aktivní stránky.  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud data byla aktualizována úspěšně, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci k provádění úloh ověření speciální data přepište.  
  
 Výchozí implementace této funkce člen zkopíruje nastavení z ovládacích prvků na stránce vlastností k členské proměnné stránky vlastností. Pokud data nebyla úspěšně aktualizována z důvodu chyby ověření (DDV) dat dialogové okno, zachová stránce fokus.  
  
 Po této – členská funkce vrátí úspěšně, zavolá rozhraní stránky [onok –](#onok) funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="onok"></a>CPropertyPage::OnOK  
 Tato funkce člen je volána rámcem, když uživatel vybere OK nebo použít nyní tlačítko ihned po volání framework [onkillactive –](#onkillactive).  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel vybere OK nebo na tlačítko použít nyní, obdrží rozhraní [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) oznámení na stránce vlastností. Volání `OnOK` nebude možné uskutečnit při volání [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) vzhledem k tomu, že stránka vlastností neodešle oznámení v takovém případě.  
  
 Funkci člena na implementaci Další chování, které jsou specifické pro stránku aktuálně aktivní uživatel zavře celý vlastností přepište.  
  
 Výchozí implementace této funkce člen označí stránce jako "clean" tak, aby odrážela, aby data byla aktualizována v `OnKillActive` funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="onquerycancel"></a>CPropertyPage::OnQueryCancel  
 Tento člen funkce je volána rámcem, když uživatel klikne na tlačítko Storno a před zrušit akci neproběhla.  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **FALSE** aby se zabránilo operace zrušení nebo TRUE tak, aby ji.  
  
### <a name="remarks"></a>Poznámky  
 Přepište tuto členskou funkci k určení akce, které program provede, když uživatel klikne na tlačítko Storno.  
  
 Výchozí implementaci `OnQueryCancel` vrátí **TRUE**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="onreset"></a>CPropertyPage::OnReset  
 Tento člen funkce je volána rámcem, když uživatel vybere na tlačítko Storno.  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>Poznámky  
 Když tato funkce volá framework, se zahodí změny na všechny stránky vlastností, které byly provedeny uživatelem dříve výběr tlačítko použít a seznamu vlastností zachová fokus.  
  
 Přepsání této funkci člen můžete určit, jakou akci provede program, když uživatel klikne na tlačítko Storno.  
  
 Výchozí implementaci `OnReset` neprovede žádnou akci.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertyPage::OnCancel](#oncancel).  
  
##  <a name="onsetactive"></a>CPropertyPage::OnSetActive  
 Tento člen funkce je volána rámcem, když na stránce je volená uživatelem a stránkou bude aktivní.  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně nastaven active; stránky jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci k provádění úloh, když je aktivován stránky přepište. Přepsání této funkce člen by volat výchozí verze obvykle po aktualizaci datových členů, tak, aby ji aktualizovat ovládací prvky stránky nová data.  
  
 Výchozí implementace vytvoří okno pro stránku, není-li dřív vytvořili a umožňuje aktivní stránky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).  
  
##  <a name="onwizardback"></a>CPropertyPage::OnWizardBack  
 Tento člen funkce je volána rámcem, když uživatel klikne na tlačítko Zpět na průvodce.  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 0 pro automatický přechod na další stránku. -1 zabránit ve změně stránky. Přejít na stránku než další, vrátí identifikátor dialogu, který se má zobrazit.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci zadat některá z akcí, které musí uživatel provést při stisknutí tlačítka Zpět přepište.  
  
 Další informace o tom, aby typ průvodce vlastností najdete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish  
 Tento člen funkce je volána rámcem, když uživatel klikne na tlačítko Dokončit v průvodci.  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud seznamu vlastností je zrušen po dokončení Průvodce; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel klikne **Dokončit** volá tuto funkci, tlačítko v průvodci, rozhraní; když `OnWizardFinish` vrátí **TRUE** (nenulovou hodnotu), seznam vlastností se může být zničený (ale není ve skutečnosti zničení). Volání `DestroyWindow` se zničit okno vlastností. Nevolejte `DestroyWindow` z `OnWizardFinish`; to tak může způsobit poškození haldy nebo jiné chyby.  
  
 Člen funkci zadat některá z akcí, které musí uživatel provést při stisknutí tlačítka Dokončit můžete přepsat. Při přepisování tuto funkci, vrátí **FALSE** zabránit jeho zničení seznamu vlastností.  
  
 Další informace o zprávy oznámení po stisknutí tlačítka Dokončit v seznamu vlastností průvodce najdete v tématu [PSN_WIZFINISH](http://msdn.microsoft.com/library/windows/desktop/bb774571) ve Windows SDK.  
  
 Další informace o tom, aby typ průvodce vlastností najdete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="onwizardnext"></a>CPropertyPage::OnWizardNext  
 Tento člen funkce je volána rámcem, když uživatel klikne na tlačítko Další v průvodci.  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 0 pro automatický přechod na další stránku. -1 zabránit ve změně stránky. Přejít na stránku než další, vrátí identifikátor dialogu, který se má zobrazit.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci zadat některá z akcí, které musí uživatel provést při stisknutí tlačítka Další přepište.  
  
 Další informace o tom, aby typ průvodce vlastností najdete v tématu [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]  
  
##  <a name="querysiblings"></a>CPropertyPage::QuerySiblings  
 Volání této funkce člen přeposílat zprávy na každou stránku v seznamu vlastností.  
  
```  
LRESULT QuerySiblings(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `wParam`  
 Určuje další informace závislé na zprávy.  
  
 `lParam`  
 Určuje další informace závislé na zprávu  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu ze stránky v seznamu vlastností, nebo 0, pokud všechny stránky vrátit hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud na stránce vrátí nenulovou hodnotu, seznam vlastností není odeslat zprávu pro následné stránky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="setmodified"></a>CPropertyPage::SetModified  
 Volání této funkce člen k povolení nebo zakázání teď použít tlačítko, založené na tom, jestli bude použito nastavení na stránce vlastností příslušný externí objekt.  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bChanged`  
 **Hodnota TRUE,** k označení, že od poslední se uplatňují; byl změněn nastavení stránky vlastností **FALSE** že aplikovala nastavení vlastností stránky, nebo třeba ji ignorovat.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework udržuje sledování, které jsou stránky "nečisté", který je, stránky vlastností, pro které se mají volat **SetModified (TRUE)**. Tlačítko použít teď bude vždy povolená při volání **SetModified (TRUE)** pro jednu ze stránek. Tlačítko použít teď bude zakázáno, při volání **SetModified (FALSE)** pro jednu ze stránek, ale jen pokud žádný z dalších stránek je "nekonzistentní."  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL1 MFC](../../visual-cpp-samples.md)   
 [Ukázka CMNCTRL2 MFC](../../visual-cpp-samples.md)   
 [Ukázka MFC PROPDLG](../../visual-cpp-samples.md)   
 [Ukázka MFC SNAPVW](../../visual-cpp-samples.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cpropertysheet – třída](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
