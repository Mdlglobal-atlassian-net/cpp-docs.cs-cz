---
title: CDataExchange – třída
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
ms.openlocfilehash: 73319ad898bfebf4caf191954ebb3935bd4ebce9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321957"
---
# <a name="cdataexchange-class"></a>CDataExchange – třída

Podporuje rutiny výměny dat dialogu (DDX) a ověření dat dialogových dat (DDV) používané třídami Microsoft Foundation.

## <a name="syntax"></a>Syntaxe

```
class CDataExchange
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|Vytvoří `CDataExchange` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDataExchange::Selhání](#fail)|Nazývá se při ověření se nezdaří. Obnoví fokus na předchozí ovládací prvek a vyvolá výjimku.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Připraví zadaný ovládací prvek pro výměnu dat nebo ověření. Používá se pro ovládací prvky bez úprav.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Připraví zadaný ovládací prvek úprav pro výměnu dat nebo ověření.|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Připraví zadaný ovládací prvek OLE pro výměnu dat nebo ověření. Používá se pro ovládací prvky bez úprav.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Příznak pro směr DDX a DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|Dialogové okno nebo okno, ve kterém probíhá výměna dat.|

## <a name="remarks"></a>Poznámky

`CDataExchange`nemá základní třídu.

Tuto třídu použijte, pokud píšete rutiny výměny dat pro vlastní datové typy nebo ovládací prvky nebo pokud píšete vlastní rutiny ověření dat. Další informace o psaní vlastních rutin DDX a DDV naleznete [v technické poznámce 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled DDX a DDV najdete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and Dialog [Boxes](../../mfc/dialog-boxes.md).

Objekt `CDataExchange` poskytuje kontextové informace potřebné pro DDX a DDV. Příznak *m_bSaveAndValidate* je FALSE, pokud se ddx používá k vyplnění počátečních hodnot dialogových ovládacích prvků z datových členů. Příznak *m_bSaveAndValidate* je TRUE, pokud se ddx používá k nastavení aktuálních hodnot dialogových ovládacích prvků do datových členů a při použití ddv k ověření datových hodnot. Pokud se ověření DDV nezdaří, postup DDV zobrazí okno se zprávou vysvětlující vstupní chybu. Procedura DDV pak `Fail` zavolá, aby se fokus obnovil na problematický ovládací prvek a vyvolal výjimku pro zastavení procesu ověření.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDataExchange`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange::CDataExchange

Volání této členské funkce `CDataExchange` k vytvoření objektu.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Parametry

*pDlgWnd*<br/>
Ukazatel na nadřazené okno, které obsahuje ovládací prvek. Obvykle se jedná o [cDialog](../../mfc/reference/cdialog-class.md)-odvozený objekt.

*bSaveAndValidate*<br/>
Pokud TRUE, tento objekt ověří data, pak zapíše data z ovládacích prvků do členů. Pokud false, tento objekt přesune data z členů na ovládací prvky.

### <a name="remarks"></a>Poznámky

Vytvořte `CDataExchange` objekt sami ukládat další informace v objektu výměny dat předat do okna [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) členské funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a>CDataExchange::Selhání

Rozhraní Framework volá tuto členská funkci, když se nezdaří operace ověření dat dialogu (DDV).

```
void Fail();
```

### <a name="remarks"></a>Poznámky

`Fail`obnoví fokus a výběr do ovládacího prvku, jehož ověření se nezdařilo (pokud je ovládací prvek k obnovení). `Fail`pak vyvolá výjimku typu [CUserException](../../mfc/reference/cuserexception-class.md) zastavit proces ověřování. Výjimka způsobí, že okno se zprávou vysvětlující chybu, která má být zobrazena. Po selhání ověření DDV může uživatel znovu zadat data v ovládacím prvku problematický.

Implementátoři vlastní rutiny DDV `Fail` můžete volat z jejich rutiny při ověření nezdaří.

Další informace o psaní vlastních rutin DDX a DDV naleznete [v technické poznámce 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled ddx a ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and Dialog Box [Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate

Tento příznak označuje směr operace výměny dat dialogu (DDX).

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Poznámky

Příznak je nenulový, `CDataExchange` pokud se objekt používá k přesunutí dat z ovládacích prvků dialogu do datových členů třídy dialogů poté, co uživatel ovládací prvky upraví. Příznak je nula, pokud se objekt používá k inicializaci dialogových ovládacích prvků z datových členů třídy dialogů.

Příznak je také nenulová během ověřování dat dialogového okna (DDV).

Další informace o psaní vlastních rutin DDX a DDV naleznete [v technické poznámce 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled ddx a ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and Dialog Box [Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd

Obsahuje ukazatel na [CWnd](../../mfc/reference/cwnd-class.md) objekt, pro který dialog výměna dat (DDX) nebo ověření (DDV) probíhá.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Poznámky

Tento objekt je obvykle [CDialog](../../mfc/reference/cdialog-class.md) objekt. Implementátory vlastní rutiny DDX nebo DDV můžete použít tento ukazatel získat přístup k dialogové okno, které obsahuje ovládací prvky, které pracují na.

Další informace o psaní vlastních rutin DDX a DDV naleznete [v technické poznámce 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled ddx a ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and Dialog Box [Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange::PrepareCtrl

Rozhraní Framework volá tuto členská funkci k přípravě zadaného ovládacího prvku pro výměnu dat dialogů (DDX) a ověření (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
ID ovládacího prvku, který má být připraven pro DDX nebo DDV.

### <a name="return-value"></a>Návratová hodnota

HWND ovládacího prvku připravovaného pro DDX nebo DDV.

### <a name="remarks"></a>Poznámky

Místo toho použijte [příkaz PrepareEditCtrl](#prepareeditctrl) pro ovládací prvky pro úpravy; tuto člennou funkci pro všechny ostatní ovládací prvky.

Příprava spočívá v uložení HWND ovládacího `CDataExchange` prvku ve třídě. Rozhraní framework používá tento popisovač k obnovení fokusu na dříve zaměřený ovládací prvek v případě selhání DDX nebo DDV.

Realizátoři vlastních rutin DDX nebo DDV by měli volat `PrepareCtrl` pro všechny neupravované ovládací prvky, pro které si vyměňují data prostřednictvím DDX nebo ověřují data prostřednictvím DDV.

Další informace o psaní vlastních rutin DDX a DDV naleznete [v technické poznámce 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled ddx a ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and Dialog Box [Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl

Framework volá tuto členská funkci k přípravě zadaného ovládacího prvku pro výměnu dat dialogů (DDX) a ověření (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
ID editačního ovládacího prvku, který má být připraven pro DDX nebo DDV.

### <a name="return-value"></a>Návratová hodnota

HWND editačního ovládacího prvku připravovaného pro DDX nebo DDV.

### <a name="remarks"></a>Poznámky

Místo toho použijte [příkaz PrepareCtrl](#preparectrl) pro všechny ovládací prvky bez úprav.

Příprava se skládá ze dvou věcí. Nejprve `PrepareEditCtrl` uloží HWND ovládacího `CDataExchange` prvku ve třídě. Rozhraní framework používá tento popisovač k obnovení fokusu na dříve zaměřený ovládací prvek v případě selhání DDX nebo DDV. Za `PrepareEditCtrl` druhé nastaví `CDataExchange` příznak ve třídě označuje, že ovládací prvek, jehož data jsou vyměňovány nebo ověřovány je ovládací prvek úpravy.

Realizátoři vlastních rutin DDX nebo DDV by měli volat `PrepareEditCtrl` pro všechny editační ovládací prvky, pro které si vyměňují data prostřednictvím DDX nebo ověřují data prostřednictvím DDV.

Další informace o psaní vlastních rutin DDX a DDV naleznete [v technické poznámce 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled ddx a ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and Dialog Box [Topics](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl

Rozhraní Framework volá tuto členskou funkci k přípravě zadaného ovládacího prvku OLE pro výměnu dat dialogů (DDX) a ověření (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
ID ovládacího prvku OLE, které má být připraveno pro DDX nebo DDV.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na lokalitu ovládacího prvku OLE.

### <a name="remarks"></a>Poznámky

Místo toho použijte [prepareeditctrl](#prepareeditctrl) pro ovládací prvky pro úpravy nebo [PrepareCtrl](#preparectrl) pro všechny ostatní ovládací prvky bez OLE.

Implementátory vlastní ddx nebo DDV `PrepareOleCtrl` rutiny by měl yvolat pro všechny ole ovládací prvky, pro které jsou výměnu dat prostřednictvím DDX nebo ověřování dat přes DDV.

Další informace o psaní vlastních rutin DDX a DDV naleznete [v technické poznámce 26](../../mfc/tn026-ddx-and-ddv-routines.md). Přehled ddx a ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md) and Dialog Box [Topics](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
