---
title: Třída CMFCPropertyPage
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: e493f016b6384a768935186c31e3fc71ade6382f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361756"
---
# <a name="cmfcpropertypage-class"></a>Třída CMFCPropertyPage

Třída `CMFCPropertyPage` podporuje zobrazení rozbalovacích nabídek na stránce vlastností.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Vytvoří `CMFCPropertyPage` objekt.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCPropertyPage::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|`CMFCPropertyPage::OnSetActive`|Tato členská funkce je volána rámci při výběru stránky uživatelem a stane se aktivní stránkou. (Přepíše [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Přeloží zprávy okna před jejich odesláním do funkcí [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows. Další informace a syntaxe metody naleznete [v tématu CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepíše `CPropertyPage::PreTranslateMessage`.)|

## <a name="remarks"></a>Poznámky

Třída `CMFCPropertyPage` představuje jednotlivé stránky seznamu vlastností, jinak označované jako dialogové okno karty.

Použijte `CMFCPropertyPage` třídu společně s třídou [CMFCPropertySheet.](../../mfc/reference/cmfcpropertysheet-class.md) Chcete-li použít nabídky na stránce vlastností, `CPropertyPage` nahraďte všechny výskyty třídy třídou. `CMFCPropertyPage`

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Stránka CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CmFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertypage.h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage

Vytvoří `CMFCPropertyPage` objekt.

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>Parametry

*nIDŠablona*<br/>
ID prostředku šablony pro tuto stránku.

*nIDTitulek*<br/>
ID prostředku popisku, který chcete umístit na kartu pro tuto stránku. Pokud 0, název je získán ze šablony dialogového okna pro tuto stránku. Výchozí hodnota je 0.

*lpszTemplateName*<br/>
Odkazuje na název šablony pro tuto stránku. Nemůže být null.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Další informace o parametrech konstruktoru naleznete v [tématu CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída cmfcpropertysheet](../../mfc/reference/cmfcpropertysheet-class.md)
