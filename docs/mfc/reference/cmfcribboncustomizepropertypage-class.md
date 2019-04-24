---
title: Cmfcribboncustomizepropertypage – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: 8c790ca249f34a3c9b36d1bd77dafdc4a91bd352
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237048"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Cmfcribboncustomizepropertypage – třída

Implementuje vlastní stránky pro **vlastní** dialogové okno v aplikacích založených na pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Vytvoří `CMFCRibbonCustomizePropertyPage` objektu.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Přidá vlastní kategorii **příkazy** – pole se seznamem.|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Volá se v systému, když uživatel klikne **OK** na **vlastní** dialogové okno.|

## <a name="remarks"></a>Poznámky

Pokud chcete přidat vlastní příkazy **vlastní** dialogové okno, musí zpracovat AFX_WM_ON_RIBBON_CUSTOMIZE zprávy. V popisovači zpráv vytvořit instanci `CMFCRibbonCustomizePropertyPage` objekt v zásobníku. Vytvoří seznam vlastních příkazů a následně zavolat `AddCustomCategory` pro přidání nové stránky **vlastní** dialogové okno.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCRibbonCustomizePropertyPage` objektu a chcete-li přidat vlastní kategorii.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncustomizedialog.h

##  <a name="addcustomcategory"></a>  CMFCRibbonCustomizePropertyPage::AddCustomCategory

Přidá vlastní kategorii **příkazy** – pole se seznamem.

```
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*lpszName*|[in] Určuje název vlastní kategorii.|
|*lstIDS*|[in] Obsahuje příkaz pásu karet ID má být zobrazen v kategorii Vlastní.|

### <a name="remarks"></a>Poznámky

Tato metoda přidá kategorii s názvem *lpszName* k **příkazy** – pole se seznamem. Když uživatel vybere kategorii, příkazy podle *lstIDS* se zobrazí v seznamu příkazů.

##  <a name="cmfcribboncustomizepropertypage"></a>  CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Vytvoří `CMFCRibbonCustomizePropertyPage` objektu.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parametry

*pRibbonBar*<br/>
[in] Ukazatel na ovládací prvek pásu karet, pro kterou možnosti přizpůsobení.

##  <a name="onok"></a>  CMFCRibbonCustomizePropertyPage::OnOK

Calleld systému, když uživatel klikne **OK** na **vlastní** dialogové okno.

```
virtual void OnOK();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace použije ve vybrané možnosti **vlastní** dialogové okno panelu nástrojů Rychlý přístup.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
