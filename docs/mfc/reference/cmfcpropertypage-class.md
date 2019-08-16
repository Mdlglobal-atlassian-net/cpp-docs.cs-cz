---
title: CMFCPropertyPage – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: 4be584135ef789d7fbe3b1743ac0ad6ce66ac5b1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505042"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage – třída

`CMFCPropertyPage` Třída podporuje zobrazení překryvných nabídek na stránce vlastností.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|`CMFCPropertyPage` Vytvoří objekt.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCPropertyPage::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|`CMFCPropertyPage::OnSetActive`|Tato členská funkce je volána rozhraním, když uživatel vybere stránku a bude se jednat o aktivní stránku. (Overrides [CPropertyPage –:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Další informace a syntaxi metod naleznete v tématu [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Overrides `CPropertyPage::PreTranslateMessage`.)|

## <a name="remarks"></a>Poznámky

`CMFCPropertyPage` Třída představuje jednotlivé stránky seznamu vlastností, jinak označované jako dialogové okno Karta.

Použijte třídu společně s třídou [CMFCPropertySheet.](../../mfc/reference/cmfcpropertysheet-class.md) `CMFCPropertyPage` Chcete-li použít nabídky na stránce vlastností, nahraďte všechny výskyty `CPropertyPage` třídy `CMFCPropertyPage` třídou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertypage. h

##  <a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage

`CMFCPropertyPage` Vytvoří objekt.

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
ID prostředku šablony pro tuto stránku

*nIDCaption*<br/>
ID prostředku popisku, který má být vložen na kartu pro tuto stránku. Pokud je hodnota 0, název se získá ze šablony dialogového okna pro tuto stránku. Výchozí hodnota je 0.

*lpszTemplateName*<br/>
Odkazuje na název šablony této stránky. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Další informace o parametrech konstruktoru naleznete v tématu [CPropertyPage –:: CPropertyPage –](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet – třída](../../mfc/reference/cmfcpropertysheet-class.md)
