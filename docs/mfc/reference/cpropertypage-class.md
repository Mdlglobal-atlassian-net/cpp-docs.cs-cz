---
title: CPropertyPage – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: f46566eb562f1515e98aedf938ca68b225ee1b67
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751099"
---
# <a name="cpropertypage-class"></a>CPropertyPage – třída

Představuje jednotlivé stránky seznamu vlastností, jinak označované jako dialogové okno karta.

## <a name="syntax"></a>Syntaxe

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|Vytvoří `CPropertyPage` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPropertyPage::Zrušituzavření](#canceltoclose)|Změní tlačítko OK na čtení zavřít a zakáže tlačítko Storno po neopravitelné změně na stránce seznamu modálních vlastností.|
|[CPropertyPage::Konstrukce](#construct)|Vytvoří `CPropertyPage` objekt. Použijte, `Construct` pokud chcete zadat parametry za běhu nebo pokud používáte pole.|
|[CPropertyPage::GetPSP](#getpsp)|Načte strukturu [WINDOWS PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) `CPropertyPage` přidruženou k objektu.|
|[CPropertyPage::OnApply](#onapply)|Volat rámci po klepnutí na tlačítko Použít nyní.|
|[cpropertyPage::OnCancel](#oncancel)|Volat rámci po klepnutí na tlačítko Storno.|
|[CPropertyPage::OnKillActive](#onkillactive)|Volat rámci, když aktuální stránka již není aktivní stránku. Zde proveďte ověření dat.|
|[CPropertyPage::OnOK](#onok)|Volat rámci po klepnutí na tlačítko OK, Použít nyní nebo Zavřít.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Volat rámci po klepnutí na tlačítko Storno a před zrušení proběhlo.|
|[CPropertyPage::OnReset](#onreset)|Volat rámci po klepnutí na tlačítko Storno.|
|[CPropertyPage::OnsetActive](#onsetactive)|Volat rámci při stránce je aktivní stránku.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Volat rámci při klepnutí na tlačítko Zpět při použití seznamu vlastností typu průvodce.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Volat rámci při klepnutí na tlačítko Dokončit při použití seznamu vlastností typu průvodce.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Volat rámci při klepnutí na tlačítko Další při použití seznamu vlastností typu průvodce.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Předá zprávu na každou stránku seznamu vlastností.|
|[CPropertyPage::SetModified](#setmodified)|Volání pro aktivaci nebo deaktivaci tlačítka Použít nyní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Struktura [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) systému Windows. Poskytuje přístup k základním parametrům stránky vlastností.|

## <a name="remarks"></a>Poznámky

Stejně jako u standardních dialogových oken odvozujete třídu pro `CPropertyPage` každou stránku v seznamu vlastností. Chcete-li použít `CPropertyPage`odvozené objekty, nejprve vytvořte objekt [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) a potom vytvořte objekt pro každou stránku, která se nachází v seznamu vlastností. Volání [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) pro každou stránku v listu a potom zobrazte seznam vlastností voláním [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) pro modální seznam vlastností nebo [CPropertySheet::Create](../../mfc/reference/cpropertysheet-class.md#create) for a lessless property sheet.

Můžete vytvořit typ dialogového okna karty s názvem Průvodce, který se skládá z seznamu vlastností s posloupností stránek vlastností, které uživatele provedou kroky operace, například nastavením zařízení nebo vytvořením bulletinu. V dialogovém okně karta typ průvodce stránky vlastností nemají karty a současně je zobrazena pouze jedna stránka vlastností. Namísto tlačítek OK a Použít nyní má dialogové okno karty typu průvodce také tlačítko Zpět, tlačítko Další nebo Dokončit a tlačítko Storno.

Další informace o vytvoření seznamu vlastností jako průvodce naleznete v [tématu CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Další informace o `CPropertyPage` používání objektů naleznete v článku [Seznamy vlastností a Stránky vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>CPropertyPage::Zrušituzavření

Volání této funkce po neopravitelné změny byla provedena data na stránce seznamu modální vlastností.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Poznámky

Tato funkce změní tlačítko OK na Zavřít a zakáže tlačítko Storno. Tato změna upozorní uživatele, že změna je trvalá a změny nelze zrušit.

Členská `CancelToClose` funkce neprovede nic v seznamu nemodivě vlastností, protože nemodivá seznam vlastností nemá tlačítko Storno ve výchozím nastavení.

### <a name="example"></a>Příklad

  Viz příklad pro [CPropertyPage::QuerySiblings](#querysiblings).

## <a name="cpropertypageconstruct"></a><a name="construct"></a>CPropertyPage::Konstrukce

Volání této členské funkce `CPropertyPage` k vytvoření objektu.

```cpp
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

*nIDŠablona*<br/>
ID šablony použité pro tuto stránku.

*nIDTitulek*<br/>
ID názvu, který má být umístěn na kartě pro tuto stránku. Pokud 0, název bude převzat ze šablony dialogu pro tuto stránku.

*lpszTemplateName*<br/>
Obsahuje řetězec s ukončeným hodnotou null, který je názvem prostředku šablony.

*nIDHeaderTitle*<br/>
ID názvu, který má být umístěn v názvu umístění záhlaví stránky vlastností. Ve výchozím nastavení 0.

*nIDHeaderSubTitle*<br/>
ID názvu, který má být umístěn v umístění titulků záhlaví stránky vlastností. Ve výchozím nastavení 0.

### <a name="remarks"></a>Poznámky

Objekt se zobrazí po splnění všech následujících podmínek:

- Stránka byla přidána do seznamu vlastností pomocí [cpropertysheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Byla volána funkce [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [Create](../../mfc/reference/cpropertysheet-class.md#create) listu vlastností.

- Uživatel vybral (s kartami) tuto stránku.

Volání, `Construct` pokud jeden z jiných konstruktorů třídy nebyla volána. Členská `Construct` funkce je flexibilní, protože příkaz parametru můžete ponechat prázdný a potom zadat více parametrů a konstrukce v libovolném bodě kódu.

Je nutné `Construct` použít při práci s maticí `Construct` a je nutné volat pro každého člena pole tak, aby datové členy jsou přiřazeny správné hodnoty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a>CPropertyPage::CPropertyPage

Vytvoří `CPropertyPage` objekt.

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

*nIDŠablona*<br/>
ID šablony použité pro tuto stránku.

*nIDTitulek*<br/>
ID názvu, který má být umístěn na kartě pro tuto stránku. Pokud 0, název bude převzat ze šablony dialogu pro tuto stránku.

*dwVelikost*<br/>
*lpszTemplateName* Odkazuje na řetězec obsahující název šablony pro tuto stránku. Nemůže být null.

*nIDHeaderTitle*<br/>
ID názvu, který má být umístěn v názvu umístění záhlaví stránky vlastností.

*nIDHeaderSubTitle*<br/>
ID názvu, který má být umístěn v umístění titulků záhlaví stránky vlastností.

### <a name="remarks"></a>Poznámky

Objekt se zobrazí po splnění všech následujících podmínek:

- Stránka byla přidána do seznamu vlastností pomocí [cpropertysheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Byla volána funkce [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [Create](../../mfc/reference/cpropertysheet-class.md#create) listu vlastností.

- Uživatel vybral (s kartami) tuto stránku.

Pokud máte více parametrů (například pokud používáte pole), použijte [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) místo `CPropertyPage`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a>CPropertyPage::GetPSP

Načte strukturu [WINDOWS PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) `CPropertyPage` přidruženou k objektu.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `PROPSHEETPAGE` strukturu.

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a>CPropertyPage::m_psp

`m_psp`je struktura, jejíž členové ukládají vlastnosti [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Poznámky

Pomocí této struktury inicializovat vzhled stránky vlastností po jeho vytvoření.

Další informace o této struktuře, včetně seznamu `PROPSHEETPAGE` jejích členů, naleznete v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a>CPropertyPage::OnApply

Tato členská funkce je volána rámci, když uživatel zvolí tlačítko OK nebo Použít nyní.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud jsou změny přijaty; jinak 0.

### <a name="remarks"></a>Poznámky

Když framework volá tuto funkci, jsou přijaty změny provedené na všech stránkách vlastností `OnApply` v seznamu vlastností, seznam vlastností zachová fokus a vrátí hodnotu TRUE (hodnota 1). Předtím, než `OnApply` může být volána rámci, musíte mít volal [SetModified](#setmodified) a nastavit jeho parametr na TRUE. Tím aktivujete tlačítko Použít nyní, jakmile uživatel provede změnu na stránce vlastností.

Přepsáním této členské funkce určete, jakou akci váš program provede, když uživatel klepne na tlačítko Použít nyní. Při přepsání by funkce měla vrátit hodnotu TRUE, aby přijala změny, a nepravda, aby se změny neprojevily.

Výchozí implementace `OnApply` volání `OnOK`.

Další informace o oznámení chozených, když uživatel stiskne tlačítko Použít nyní nebo OK v seznamu vlastností, najdete v [tématu PSN_APPLY](/windows/win32/Controls/psn-apply) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cPropertyPage::OnOK](#onok).

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a>cpropertyPage::OnCancel

Tato členská funkce je volána rámci při zrušení tlačítka Storno.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Poznámky

Přepište tuto člennou funkci a proveďte akce tlačítka Storno. Výchozí neguje všechny změny, které byly provedeny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a>CPropertyPage::OnKillActive

Tato členská funkce je volána rámci, pokud stránka již není aktivní stránkou.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla data úspěšně aktualizována, jinak 0.

### <a name="remarks"></a>Poznámky

Přepište tuto člennou funkci a provádějte speciální úlohy ověření dat.

Výchozí implementace této členské funkce zkopíruje nastavení z ovládacích prvků na stránce vlastností do členských proměnných stránky vlastností. Pokud data nebyla úspěšně aktualizována z důvodu chyby ověření dat dialogového okna (DDV), stránka si zachová fokus.

Po úspěšném návratu této členské funkce bude rozhraní volat funkci [OnOK](#onok) stránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a>CPropertyPage::OnOK

Tato členská funkce je volána rámci, když uživatel zvolí ok nebo použít nyní tlačítko, ihned po volání framework [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Poznámky

Když uživatel zvolí tlačítko OK nebo Použít nyní, rozhraní obdrží [PSN_APPLY](/windows/win32/Controls/psn-apply) oznámení ze stránky vlastností. Volání `OnOK` nebude provedeno, pokud zavoláte [CPropertySheet::PressButton,](../../mfc/reference/cpropertysheet-class.md#pressbutton) protože stránka vlastností neodešle oznámení v takovém případě.

Přepsat tuto členskou funkci implementovat další chování specifické pro aktuálně aktivní stránku, když uživatel zavře celý seznam vlastností.

Výchozí implementace této členské funkce označí stránku jako "čistou", aby odrážela, že data byla aktualizována ve `OnKillActive` funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a>CPropertyPage::OnQueryCancel

Tato členská funkce je volána v rámci, když uživatel klepne na tlačítko Storno a před akcí zrušení proběhla.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí funkci NEPRAVDA, chcete-li operaci zrušení zabránit, nebo funkce PRAVDA, která ji povoluje.

### <a name="remarks"></a>Poznámky

Přepsáním této členské funkce určete akci, kterou program provede, když uživatel klepne na tlačítko Storno.

Výchozí implementace `OnQueryCancel` vrátí hodnotu TRUE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a>CPropertyPage::OnReset

Tato členská funkce je volána rámci, když uživatel zvolí tlačítko Storno.

```
virtual void OnReset();
```

### <a name="remarks"></a>Poznámky

Když framework volá tuto funkci, změny na všechny stránky vlastností, které byly provedeny uživatelem dříve výběru použít nyní tlačítko jsou zahozeny a seznam vlastností zachová fokus.

Přepsáním této členské funkce určete, jakou akci program provede, když uživatel klepne na tlačítko Storno.

Výchozí implementace `OnReset` neprovede žádné provádění.

### <a name="example"></a>Příklad

  Viz příklad [cPropertyPage::OnCancel](#oncancel).

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a>CPropertyPage::OnsetActive

Tato členská funkce je volána rámci při výběru stránky uživatelem a stane se aktivní stránkou.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla stránka úspěšně nastavena aktivní; jinak 0.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci a k provádění úkolů při aktivaci stránky. Přepsání této členské funkce by obvykle volat výchozí verzi po aktualizaci datových členů, aby mohla aktualizovat ovládací prvky stránky s novými daty.

Výchozí implementace vytvoří okno pro stránku, pokud není dříve vytvořena, a z ní udělá aktivní stránku.

### <a name="example"></a>Příklad

  Viz příklad [pro CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a>CPropertyPage::OnWizardBack

Tato členská funkce je volána rámci, když uživatel klepne na tlačítko Zpět v průvodci.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Návratová hodnota

0 pro automatický postup na další stránku; -1, aby se zabránilo změně stránky. Chcete-li přejít na jinou stránku než na další, vraťte identifikátor dialogového okna, které se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepsat tuto členovou funkci určit některé akce, které uživatel musí provést při stisknutí tlačítka Zpět.

Další informace o vytvoření seznamu vlastností typu průvodce naleznete v [tématu CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish

Tato členská funkce je volána rámci, když uživatel klepne na tlačítko Dokončit v průvodci.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je seznam vlastností zničen po dokončení průvodce; jinak nula.

### <a name="remarks"></a>Poznámky

Když uživatel klepne na tlačítko **Dokončit** v průvodci, framework volá tuto funkci; pokud `OnWizardFinish` vrátí hodnotu TRUE (nenulovou hodnotu), může být seznam vlastností zničen (ale ve skutečnosti není zničen). Volání `DestroyWindow` zničit seznam vlastností. Nevolejte `DestroyWindow` z `OnWizardFinish`; to způsobí poškození haldy nebo jiné chyby.

Tuto členovou funkci můžete přepsat a určit určit určitou akci, kterou musí uživatel provést při stisknutí tlačítka Dokončit. Při přepsání této funkce vraťte hodnotu NEPRAVDA, abyste zabránili zničení seznamu vlastností.

Další informace o oznámeních odeslaných při stisknutí tlačítka Dokončit v seznamu vlastností průvodce naleznete v [PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) v sadě Windows SDK.

Další informace o vytvoření seznamu vlastností typu průvodce naleznete v [tématu CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a>CPropertyPage::OnWizardNext

Tato členská funkce je volána rámci, když uživatel klepne na tlačítko Další v průvodci.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Návratová hodnota

0 pro automatický postup na další stránku; -1, aby se zabránilo změně stránky. Chcete-li přejít na jinou stránku než na další, vraťte identifikátor dialogového okna, které se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepište tuto členovou funkci a určete nějakou akci, kterou musí uživatel provést při stisknutí tlačítka Další.

Další informace o vytvoření seznamu vlastností typu průvodce naleznete v [tématu CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a>CPropertyPage::QuerySiblings

Volání této členské funkce předat zprávu na každou stránku v seznamu vlastností.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
Určuje další informace závislé na zprávě.

*Lparam*<br/>
Určuje další informace závislé na zprávě.

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota ze stránky v seznamu vlastností nebo 0, pokud všechny stránky vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Pokud stránka vrátí nenulovou hodnotu, seznam vlastností neodešle zprávu na další stránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a>CPropertyPage::SetModified

Volání této členské funkce povolit nebo zakázat použít nyní tlačítko, na základě toho, zda nastavení na stránce vlastností by měla být použita na příslušný externí objekt.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bZměněno*<br/>
TRUE označuje, že nastavení stránky vlastností byly změněny od posledního použití; FALSE označuje, že nastavení stránky vlastností byly použity nebo by měly být ignorovány.

### <a name="remarks"></a>Poznámky

Rozhraní Framework sleduje, které stránky jsou "dirty", to znamená `SetModified( TRUE )`stránky vlastností, pro které jste volali . Tlačítko Použít nyní bude vždy povoleno, pokud zavoláte `SetModified( TRUE )` na jednu ze stránek. Tlačítko Použít nyní bude při `SetModified( FALSE )` volání jedné ze stránek zakázáno, ale pouze v případě, že žádná z ostatních stránek není "špinavá".

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Vzorek mfc PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet – třída](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
