---
title: CPropertyPage – – třída
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
ms.openlocfilehash: f9116306fd2bd6145096b055025bd4dd2075b0c1
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916881"
---
# <a name="cpropertypage-class"></a>CPropertyPage – – třída

Představuje jednotlivé stránky seznamu vlastností, jinak označované jako dialogové okno karty.

## <a name="syntax"></a>Syntaxe

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|`CPropertyPage` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPropertyPage –:: CancelToClose](#canceltoclose)|Změní tlačítko OK pro čtení zavřít a zakáže tlačítko zrušit po neopravitelné změně stránky modálního seznamu vlastností.|
|[CPropertyPage::Construct](#construct)|`CPropertyPage` Vytvoří objekt. Použijte `Construct` , pokud chcete zadat parametry za běhu, nebo pokud používáte pole.|
|[CPropertyPage::GetPSP](#getpsp)|Načte strukturu [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) Windows přidruženou `CPropertyPage` k objektu.|
|[CPropertyPage::OnApply](#onapply)|Volá se rozhraním, když se klikne na tlačítko použít.|
|[CPropertyPage::OnCancel](#oncancel)|Volá se rozhraním, když se klikne na tlačítko Storno.|
|[CPropertyPage::OnKillActive](#onkillactive)|Volá se rozhraním, když aktuální stránka už není aktivní stránkou. Sem proveďte ověření dat.|
|[CPropertyPage::OnOK](#onok)|Volá se rozhraním, když se klikne na tlačítko OK, použít nebo zavřít.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Volá se rozhraním, když se klikne na tlačítko Storno a před tím, než bylo zrušení provedeno.|
|[CPropertyPage::OnReset](#onreset)|Volá se rozhraním, když se klikne na tlačítko Storno.|
|[CPropertyPage::OnSetActive](#onsetactive)|Volá se rozhraním, když se stránka stane aktivní stránkou.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Volá se rozhraním, když se klikne na tlačítko zpět při použití seznamu vlastností Průvodce-typ.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Volá se rozhraním, když se klikne na tlačítko Dokončit při použití seznamu vlastností Průvodce-typ.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Volá se rozhraním, když se klikne na tlačítko Další při použití seznamu vlastností Průvodce-typ.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Přepošle zprávu na každou stránku seznamu vlastností.|
|[CPropertyPage::SetModified](#setmodified)|Zavolejte na aktivovat nebo deaktivovat tlačítko použít nyní.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Struktura [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) systému Windows. Poskytuje přístup k základním parametrům stránky vlastností.|

## <a name="remarks"></a>Poznámky

Stejně jako u standardních dialogových oken odvozujete třídu `CPropertyPage` od pro každou stránku v seznamu vlastností. Chcete- `CPropertyPage`li použít objekty odvozené od, vytvořte nejprve objekt [CPropertySheet –](../../mfc/reference/cpropertysheet-class.md) a pak vytvořte objekt pro každou stránku, která se nachází v seznamu vlastností. Zavolejte [CPropertySheet –:: addPage](../../mfc/reference/cpropertysheet-class.md#addpage) pro každou stránku v listu a potom zobrazte seznam vlastností voláním [CPropertySheet –::D omodal](../../mfc/reference/cpropertysheet-class.md#domodal) pro modální seznam vlastností nebo [CPropertySheet –:: Create](../../mfc/reference/cpropertysheet-class.md#create) pro nemodální seznam vlastností.

Můžete vytvořit typ dialogového okna karta s názvem průvodce, který se skládá ze seznamu vlastností se sekvencí stránek vlastností, které provedou uživatele prostřednictvím kroků operace, jako je například nastavení zařízení nebo vytvoření bulletinu. V dialogovém okně Průvodce – typ karty stránky vlastností nejsou karty a v jednu chvíli je viditelná jenom jedna stránka vlastností. Místo toho, abyste měli tlačítka OK a použít nyní, má dialogové okno Karta typ průvodce tlačítko zpět, tlačítko Další nebo dokončit a tlačítko Storno.

Další informace o tom, jak vytvořit seznam vlastností jako průvodce, najdete v tématu [CPropertySheet –:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Další informace o používání `CPropertyPage` objektů naleznete v článku seznam [vlastností a stránky vlastností](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="canceltoclose"></a>CPropertyPage –:: CancelToClose

Volání této funkce poté, co byla provedena neopravitelná změna na data na stránce modálního seznamu vlastností.

```
void CancelToClose();
```

### <a name="remarks"></a>Poznámky

Tato funkce změní tlačítko OK na Zavřít a zakáže tlačítko Storno. Tato změna upozorní uživatele, že změna je trvalá a změny nelze zrušit.

`CancelToClose` Členská funkce neprovede v nemodálním seznamu vlastností nic, protože nemodální seznam vlastností nemá ve výchozím nastavení tlačítko Storno.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertyPage –:: QuerySiblings](#querysiblings).

##  <a name="construct"></a>CPropertyPage –:: Construct

Chcete-li vytvořit `CPropertyPage` objekt, zavolejte tuto členskou funkci.

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

*nIDTemplate*<br/>
ID šablony použité pro tuto stránku

*nIDCaption*<br/>
ID názvu, který se má umístit na kartu pro tuto stránku Pokud je hodnota 0, název bude proveden ze šablony dialogového okna pro tuto stránku.

*lpszTemplateName*<br/>
Obsahuje řetězec zakončený hodnotou null, který je názvem prostředku šablony.

*nIDHeaderTitle*<br/>
ID názvu, který se má umístit do umístění názvu záhlaví stránky vlastností Ve výchozím nastavení 0.

*nIDHeaderSubTitle*<br/>
ID názvu, který se má umístit do umístění podnadpisu záhlaví stránky vlastností Ve výchozím nastavení 0.

### <a name="remarks"></a>Poznámky

Objekt se zobrazí po splnění všech následujících podmínek:

- Stránka byla přidána do seznamu vlastností pomocí [CPropertySheet –:: addPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Byla volána funkce [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [Create](../../mfc/reference/cpropertysheet-class.md#create) v seznamu vlastností.

- Uživatel vybral tuto stránku (na kartách).

Volejte `Construct` , pokud nebyl volán jeden z konstruktorů třídy. `Construct` Členská funkce je flexibilní, protože můžete nechat příkaz Parameter prázdný a pak v jakémkoli bodě kódu zadat více parametrů a konstrukce.

Je nutné použít `Construct` při práci s poli a je nutné zavolat `Construct` pro každého člena pole tak, aby datovým členům byly přiřazeny správné hodnoty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>CPropertyPage –:: CPropertyPage –

`CPropertyPage` Vytvoří objekt.

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

*nIDTemplate*<br/>
ID šablony použité pro tuto stránku

*nIDCaption*<br/>
ID názvu, který se má umístit na kartu pro tuto stránku Pokud je hodnota 0, název bude proveden ze šablony dialogového okna pro tuto stránku.

*nenulového dwSize funkci*<br/>
*lpszTemplateName* Odkazuje na řetězec obsahující název šablony pro tuto stránku. Nemůže mít hodnotu NULL.

*nIDHeaderTitle*<br/>
ID názvu, který se má umístit do umístění názvu záhlaví stránky vlastností

*nIDHeaderSubTitle*<br/>
ID názvu, který se má umístit do umístění podnadpisu záhlaví stránky vlastností

### <a name="remarks"></a>Poznámky

Objekt se zobrazí po splnění všech následujících podmínek:

- Stránka byla přidána do seznamu vlastností pomocí [CPropertySheet –:: addPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- Byla volána funkce [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) nebo [Create](../../mfc/reference/cpropertysheet-class.md#create) v seznamu vlastností.

- Uživatel vybral tuto stránku (na kartách).

Pokud máte více parametrů (například pokud používáte pole), použijte [CPropertySheet –:: Construct](../../mfc/reference/cpropertysheet-class.md#construct) namísto `CPropertyPage`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>CPropertyPage –:: GetPSP

Načte strukturu [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2) Windows přidruženou `CPropertyPage` k objektu.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `PROPSHEETPAGE` strukturu.

##  <a name="m_psp"></a>  CPropertyPage::m_psp

`m_psp`je struktura, jejíž členové ukládají vlastnosti [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Poznámky

Tuto strukturu použijte k inicializaci vzhledu stránky vlastností poté, co je vytvořena.

Další informace o této struktuře, včetně výpisu jejích členů, naleznete v části `PROPSHEETPAGE` v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>CPropertyPage –:: Apply

Tato členská funkce je volána rozhraním, když uživatel zvolí tlačítko OK nebo použít nyní.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud jsou změny přijaty; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Když rozhraní volá tuto funkci, změny provedené na všech stránkách vlastností v seznamu vlastností jsou přijímány, seznam vlastností zachová fokus a `OnApply` vrátí hodnotu true (hodnota 1). Předtím `OnApply` , než může být rozhraní Voláno rozhraním, je nutné volat [SetModified](#setmodified) a nastavit jeho parametr na hodnotu true. Tím se aktivuje tlačítko použít nyní, jakmile uživatel provede změnu na stránce vlastností.

Přepište tuto členskou funkci, pokud chcete určit akci, kterou program provede, když uživatel klikne na tlačítko použít nyní. Při přepsání by měla funkce vracet hodnotu TRUE, aby přijímala změny a nedocházelo k tomu, aby se změny projevily.

Výchozí implementace `OnApply` volání `OnOK`.

Další informace o oznamovacích zprávách odeslaných po stisknutí tlačítka použít nyní nebo OK v seznamu vlastností naleznete v tématu [PSN_APPLY](/windows/desktop/Controls/psn-apply) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertyPage –:: OnOK –](#onok).

##  <a name="oncancel"></a>CPropertyPage –::-Cancel

Tato členská funkce je volána rozhraním, když je vybráno tlačítko Storno.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci pro provádění akcí tlačítek Storno. Výchozí negace všech změn, které byly provedeny.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive

Tato členská funkce je volána rozhraním, když stránka již není aktivní stránkou.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla data úspěšně aktualizována, jinak 0.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci pro provádění speciálních úloh ověření dat.

Výchozí implementace této členské funkce kopíruje nastavení z ovládacích prvků na stránce vlastností na členské proměnné stránky vlastností. Pokud se data úspěšně neaktualizovala z důvodu chyby ověření dat dialogového okna (DDV), stránka si zachová fokus.

Po úspěšném vrácení této členské funkce bude rozhraní volat funkci [OnOK –](#onok) stránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>CPropertyPage –:: OnOK –

Tato členská funkce je volána rozhraním, když uživatel zvolí tlačítko OK nebo použít nyní hned po volání rozhraní [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Poznámky

Když uživatel zvolí tlačítko OK nebo použít nyní, rozhraní obdrží oznámení [PSN_APPLY](/windows/desktop/Controls/psn-apply) ze stránky vlastností. Volání se `OnOK` neprovede, pokud zavoláte [CPropertySheet –::P ressbutton](../../mfc/reference/cpropertysheet-class.md#pressbutton) , protože stránka vlastností neposílá oznámení v takovém případě.

Přepište tuto členskou funkci pro implementaci dalšího chování, které je specifické pro aktuálně aktivní stránku, když uživatel vynechává celý seznam vlastností.

Výchozí implementace této členské funkce označí stránku jako "vyčistit", aby odrážela to, že byla data aktualizována ve `OnKillActive` funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel

Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Storno a před tím, než dojde k akci zrušit.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu FALSE, chcete-li zabránit operaci zrušení nebo hodnotě TRUE, aby ji bylo možné použít.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci přepište, pokud chcete určit akci, kterou program provede, když uživatel klikne na tlačítko Storno.

Výchozí implementace `OnQueryCancel` funkce vrátí hodnotu true.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>CPropertyPage –::-Reset

Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Storno.

```
virtual void OnReset();
```

### <a name="remarks"></a>Poznámky

Když rozhraní volá tuto funkci, změny všech stránek vlastností, které byly provedeny uživatelem dříve výběr tlačítka použít nyní, jsou zahozeny a seznam vlastností zachová fokus.

Tuto členskou funkci přepište, pokud chcete určit, jakou akci program provede, když uživatel klikne na tlačítko Storno.

Výchozí implementace `OnReset` neprovede žádnou akci.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertyPage –::-Cancel](#oncancel).

##  <a name="onsetactive"></a>CPropertyPage –:: OnSetActive

Tato členská funkce je volána rozhraním, když uživatel vybere stránku a bude se jednat o aktivní stránku.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla stránka úspěšně nastavena jako aktivní; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci, aby se prováděly úlohy při aktivaci stránky. Vaše přepsání této členské funkce by obvykle volalo výchozí verzi po aktualizaci datových členů, aby mohla aktualizovat ovládací prvky stránky s novými daty.

Výchozí implementace vytvoří okno pro stránku, pokud se dřív nevytvořilo, a stane se aktivní stránkou.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

##  <a name="onwizardback"></a>CPropertyPage –:: OnWizardBack

Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko zpět v průvodci.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Návratová hodnota

0 pro automatické přechodu na další stránku; -1, pokud chcete zabránit změně stránky. Chcete-li přejít na jinou stránku, než na další, vraťte identifikátor dialogového okna, který se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci, pokud chcete určit určitou akci, kterou musí uživatel provést při stisknutí tlačítka zpět.

Další informace o tom, jak vytvořit seznam vlastností typu průvodce, naleznete v tématu [CPropertySheet –:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>CPropertyPage –:: OnWizardFinish

Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Dokončit v průvodci.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je seznam vlastností zničen po dokončení Průvodce; jinak nula.

### <a name="remarks"></a>Poznámky

Když uživatel klikne na tlačítko **Dokončit** v průvodci, rozhraní zavolá tuto funkci. Pokud `OnWizardFinish` vrátí hodnotu true (nenulovou hodnotu), seznam vlastností může být zničen (ale není ve skutečnosti zničen). Zavolá `DestroyWindow` se, aby se zničil seznam vlastností. Nevolejte `DestroyWindow` z `OnWizardFinish`. při tomto důsledku dojde k poškození haldy nebo k jiným chybám.

Tuto členskou funkci můžete přepsat a určit tak určitou akci, kterou musí uživatel provést při stisknutí tlačítka Dokončit. Při přepsání této funkce vrátí hodnotu FALSE, aby se zabránilo zničení seznamu vlastností.

Další informace o oznamovacích zprávách odeslaných po stisknutí tlačítka dokončit v seznamu vlastností průvodce najdete v tématu [PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) v Windows SDK.

Další informace o tom, jak vytvořit seznam vlastností typu průvodce, naleznete v tématu [CPropertySheet –:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>CPropertyPage –:: OnWizardNext

Tato členská funkce je volána rozhraním, když uživatel klikne na tlačítko Další v průvodci.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Návratová hodnota

0 pro automatické přechodu na další stránku; -1, pokud chcete zabránit změně stránky. Chcete-li přejít na jinou stránku, než na další, vraťte identifikátor dialogového okna, který se má zobrazit.

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci, pokud chcete určit určitou akci, kterou musí uživatel provést při stisknutí tlačítka Další.

Další informace o tom, jak vytvořit seznam vlastností typu průvodce, naleznete v tématu [CPropertySheet –:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings

Tuto členskou funkci volejte pro přeposlání zprávy na každou stránku v seznamu vlastností.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
Určuje další informace závislé na zprávě.

*lParam*<br/>
Určuje další informace závislé na zprávě.

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota ze stránky v seznamu vlastností nebo 0, pokud všechny stránky vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Pokud stránka vrátí nenulovou hodnotu, seznam vlastností zprávu nepošle na další stránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>CPropertyPage –:: SetModified

Voláním této členské funkce povolíte nebo zakážete tlačítko použít nyní na základě toho, zda by mělo být nastavení na stránce vlastností použito na příslušný externí objekt.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Parametry

*bChanged*<br/>
TRUE pro indikaci, že nastavení stránky vlastností bylo od posledního použití změněno; FALSE pro indikaci, že nastavení stránky vlastností bylo použito nebo by mělo být ignorováno.

### <a name="remarks"></a>Poznámky

Rozhraní uchovává přehled o tom, které stránky jsou "dirty", což jsou stránky vlastností, pro které jste `SetModified( TRUE )`volali. Tlačítko použít nyní bude vždy povoleno, pokud zavoláte `SetModified( TRUE )` jednu ze stránek. Tlačítko použít nyní bude zakázáno při volání `SetModified( FALSE )` na jednu ze stránek, ale pouze v případě, že žádná z ostatních stránek není "dirty".

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Viz také:

[CMNCTRL1 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CMNCTRL2 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[PROPDLG Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[SNAPVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet – třída](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
