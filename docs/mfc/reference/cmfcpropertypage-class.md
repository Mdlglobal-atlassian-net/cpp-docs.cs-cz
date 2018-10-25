---
title: Cmfcpropertypage – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 583bb644a50bf1bfbd6b17393fbf86ef1963adc4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053341"
---
# <a name="cmfcpropertypage-class"></a>Cmfcpropertypage – třída

`CMFCPropertyPage` Třídy podporuje zobrazení místních nabídek na stránce vlastností.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Vytvoří `CMFCPropertyPage` objektu.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCPropertyPage::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|`CMFCPropertyPage::OnSetActive`|Tato členská funkce je voláno rozhraním při stránky je vybrán uživatelem a stane aktivní stránkou. (Přepíše [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. Další informace a syntaxe využívající metody, naleznete v tématu [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepíše `CPropertyPage::PreTranslateMessage`.)|

## <a name="remarks"></a>Poznámky

`CMFCPropertyPage` Třída představuje jednotlivé stránky seznamu vlastností, jinak známé jako dialogové okno Karta.

Použití `CMFCPropertyPage` třídy společně s [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) třídy. Abyste mohli použít nabídek na stránce vlastností, nahraďte všechny výskyty `CPropertyPage` třídy s `CMFCPropertyPage` třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage –](../../mfc/reference/cpropertypage-class.md)

[Cmfcpropertypage –](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertypage.h

##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage

Vytvoří `CMFCPropertyPage` objektu.

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
ID prostředku šablony pro tuto stránku.

*nIDCaption*<br/>
ID prostředku popisku se umístí na kartě pro tuto stránku. Pokud je 0, název se získávají z šablony dialogového okna pro tuto stránku. Výchozí hodnota je 0.

*lpszTemplateName*<br/>
Odkazuje na název šablony pro tuto stránku. Nemůže mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Další informace o parametrech konstruktoru, naleznete v tématu [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet – třída](../../mfc/reference/cmfcpropertysheet-class.md)
