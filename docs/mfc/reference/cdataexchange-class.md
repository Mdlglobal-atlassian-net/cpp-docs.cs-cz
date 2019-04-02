---
title: CDataExchange Class
ms.date: 11/04/2016
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: 0e7a9d429acb1acd72942e5f10ac0815232ddc69
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776307"
---
# <a name="cdataexchange-class"></a>CDataExchange Class

Podporuje výměna dat dialogových oken (DDX) a rutiny (DDV) ověřování dat dialogového okna používané v rámci tříd Microsoft Foundation.

## <a name="syntax"></a>Syntaxe

```
class CDataExchange
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|Vytvoří `CDataExchange` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDataExchange::Fail](#fail)|Volá se, když se ověřování nezdaří. Obnoví fokus na předchozí ovládací prvek a vyvolá výjimku.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Připraví zadaný ovládací prvek pro výměnu dat nebo ověření. Použití pro ovládací prvky nonedit.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Připraví zadané textové pole pro výměnu dat nebo ověření.|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Určený ovládací prvek OLE připraví pro výměnu dat nebo ověření. Použití pro ovládací prvky nonedit.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Příznak směru DDX a DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|Dialogové okno nebo okno, kde data exchange probíhá.|

## <a name="remarks"></a>Poznámky

`CDataExchange` nemá základní třídu.

Tuto třídu použít, pokud píšete rutiny výměny dat pro vlastní datové typy nebo ovládací prvky, nebo pokud vytváříte vlastní rutiny ověřování dat. Další informace o psaní vlastních rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV, naleznete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [dialogových oknech](../../mfc/dialog-boxes.md).

A `CDataExchange` objekt poskytuje kontextové informace potřebné pro DDX a DDV trvat umístit. Příznak *m_bSaveAndValidate* je FALSE při DDX slouží k naplnění počáteční hodnoty ovládací prvky dialogového okna z datové členy. Příznak *m_bSaveAndValidate* hodnotu TRUE, pokud DDX slouží k nastavení aktuální hodnoty ovládací prvky dialogového okna do datové členy a kdy DDV slouží k ověření datových hodnot. Pokud DDV ověření nezdaří, zobrazí se postup DDV okno se zprávou s vysvětlením vstupních chyb. Pak zavolá postup DDV `Fail` resetovat fokus na problematický ovládací prvek a vyvolat výjimku zastavte sledovací proces ověřování.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDataExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cdataexchange"></a>  CDataExchange::CDataExchange

Voláním této členské funkce k vytvoření `CDataExchange` objektu.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Parametry

*pDlgWnd*<br/>
Ukazatel do nadřazeného okna, která obsahuje ovládací prvek. Obvykle se jedná [CDialog](../../mfc/reference/cdialog-class.md)-odvozenému objektu.

*bSaveAndValidate*<br/>
Při hodnotě TRUE se tento objekt ověřuje data a pak zapíše data z ovládacích prvků členů. Pokud má hodnotu FALSE, tento objekt přesun dat z členů na ovládací prvky.

### <a name="remarks"></a>Poznámky

Vytvoření `CDataExchange` objekt sami sebe k ukládání dalších informací datového objektu exchange k předání do vašeho okna [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

##  <a name="fail"></a>  CDataExchange::Fail

Rozhraní volá tuto členskou funkci, pokud selže operace s daty ověření (DDV) dialogové okno.

```
void Fail();
```

### <a name="remarks"></a>Poznámky

`Fail` Obnoví fokus a výběru ovládacího prvku, jejichž ověření se nezdařilo (Pokud je ovládací prvek pro obnovení). `Fail` následně vyvolává výjimku typu [cuserexception –](../../mfc/reference/cuserexception-class.md) zastavte sledovací proces ověřování. Výjimky způsobí, že okno se zprávou s vysvětlením chyb, který se má zobrazit. Po ověření DDV nezdaří, uživatel může znovu dat v ovládacím prvku problematické.

Můžete volat implementors vlastní rutiny DDV `Fail` z jejich rutiny, když se ověřování nezdaří.

Další informace o psaní vlastních rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV, naleznete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [Dialog Box témata](../../mfc/dialog-boxes.md).

##  <a name="m_bsaveandvalidate"></a>  CDataExchange::m_bSaveAndValidate

Tento příznak určuje směr operace s daty exchange (DDX) dialogové okno.

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Poznámky

Příznaku je nenulová Pokud `CDataExchange` objektu se používá k přesunu dat z ovládací prvky dialogového okna na datové členy třídy dialogového okna, jakmile uživatel upravuje ovládací prvky. Příznak je nula, pokud objekt se používá k inicializaci dialogového okna ovládacích prvků z datové členy třídy dialogového okna.

Příznak je nenulový také při ověřování dat dialogového okna (DDV).

Další informace o psaní vlastních rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV, naleznete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [Dialog Box témata](../../mfc/dialog-boxes.md).

##  <a name="m_pdlgwnd"></a>  CDataExchange::m_pDlgWnd

Obsahuje ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objektu, pro který dialog výměnu dat (DDX) nebo ověřování (DDV) probíhat.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Poznámky

Tento objekt je obvykle [CDialog](../../mfc/reference/cdialog-class.md) objektu. Implementors vlastní rutiny DDX a DDV můžete použít k získání přístupu do dialogového okna, která obsahuje ovládací prvky jsou nasazeny na tento ukazatel.

Další informace o psaní vlastních rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV, naleznete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [Dialog Box témata](../../mfc/dialog-boxes.md).

##  <a name="preparectrl"></a>  CDataExchange::PrepareCtrl

Rozhraní volá tuto funkci člena zadaný ovládací prvek Příprava výměna dat dialogových oken (DDX) a ověřování (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
ID ovládacího prvku abyste byli připraveni DDX a DDV

### <a name="return-value"></a>Návratová hodnota

HWND určené pro DDX a DDV ovládacího prvku.

### <a name="remarks"></a>Poznámky

Použít [PrepareEditCtrl](#prepareeditctrl) místo pro ovládacích prvcích pro úpravy; použijte pro všechny ostatní ovládací prvky tuto členskou funkci.

Příprava se skládá z ovládacího prvku HWND v ukládání `CDataExchange` třídy. Rozhraní používá tento ovladač k obnovení dříve cílené ovládacího prvku v případě selhání DDX a DDV fokus.

Implementors vlastní rutiny DDX a DDV by měly volat `PrepareCtrl` pro všechny ovládací prvky bez úprav, pro které výměna dat prostřednictvím DDX nebo ověřování dat prostřednictvím DDV.

Další informace o psaní vlastních rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV, naleznete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [Dialog Box témata](../../mfc/dialog-boxes.md).

##  <a name="prepareeditctrl"></a>  CDataExchange::PrepareEditCtrl

Rozhraní volá tuto funkci člena zadané textové pole Příprava výměna dat dialogových oken (DDX) a ověřování (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
ID ovládacího prvku pro úpravy se připravit DDX a DDV.

### <a name="return-value"></a>Návratová hodnota

HWND určené pro DDX a DDV ovládacího prvku pro úpravy.

### <a name="remarks"></a>Poznámky

Použití [PrepareCtrl](#preparectrl) místo pro všechny ovládací prvky bez úprav.

Příprava se skládá ze dvou kroků. Nejprve je potřeba `PrepareEditCtrl` ukládá ovládacího prvku HWND ve `CDataExchange` třídy. Rozhraní používá tento ovladač k obnovení dříve cílené ovládacího prvku v případě selhání DDX a DDV fokus. Druhý, `PrepareEditCtrl` nastaví příznak, který `CDataExchange` třída, která označuje, že ovládací prvek, jehož data se vyměňují nebo ověření je ovládací prvek upravit.

Implementors vlastní rutiny DDX a DDV by měly volat `PrepareEditCtrl` pro všechny ovládací prvky, pro které výměna dat prostřednictvím DDX nebo ověřování dat prostřednictvím DDV úprav.

Další informace o psaní vlastních rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV, naleznete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [Dialog Box témata](../../mfc/dialog-boxes.md).

##  <a name="prepareolectrl"></a>  CDataExchange::PrepareOleCtrl

Rozhraní volá tuto funkci člena zadaný ovládací prvek OLE Příprava výměna dat dialogových oken (DDX) a ověřování (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
ID ovládacího prvku OLE se připravit DDX a DDV.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na ovládací prvek webu OLE.

### <a name="remarks"></a>Poznámky

Použití [PrepareEditCtrl](#prepareeditctrl) místo pro ovládacích prvcích pro úpravy nebo [PrepareCtrl](#preparectrl) pro všechny ostatní ovládací prvky jiných než OLE.

Implementors vlastní rutiny DDX a DDV by měly volat `PrepareOleCtrl` pro všechny ovládací prvky OLE, pro které výměna dat prostřednictvím DDX nebo ověřování dat prostřednictvím DDV.

Další informace o psaní vlastních rutiny DDX a DDV najdete v tématu [Technická poznámka 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV, naleznete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md) a [Dialog Box témata](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
