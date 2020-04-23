---
title: Třída CMFCAPřizpůsobení vlastností karty
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
ms.openlocfilehash: 57fbd1e1f574beebff8baab014e7ab615f56333f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754172"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Třída CMFCAPřizpůsobení vlastností karty

Implementuje vlastní stránku pro dialogové okno **Přizpůsobit** v aplikacích založených na pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCRibbonRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Vytvoří `CMFCRibbonCustomizePropertyPage` objekt.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Přidá vlastní kategorii do pole se **seznamem Příkazy.**|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Volat systém, když uživatel klepne na **TLAČÍTKO OK** v dialogovém okně **Přizpůsobit.**|

## <a name="remarks"></a>Poznámky

Pokud chcete do dialogového okna **Přizpůsobit** přidat vlastní příkazy, musíte zpracovat zprávu AFX_WM_ON_RIBBON_CUSTOMIZE. V obslužné rutině `CMFCRibbonCustomizePropertyPage` zprávy vytvořte instanci objektu v zásobníku. Vytvořte seznam vlastních příkazů a `AddCustomCategory` pak voláním přidejte novou stránku do dialogového okna **Přizpůsobit.**

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCRibbonCustomizePropertyPage` vytvořit objekt a přidat vlastní kategorii.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Stránka CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CmFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CmFCFcRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory

Přidá vlastní kategorii do pole se **seznamem Příkazy.**

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Popis|
|*název lpsz*|[v] Určuje název vlastní kategorie.|
|*lstIDS*|[v] Obsahuje ID příkazů pásu karet, která se mají zobrazit ve vlastní kategorii.|

### <a name="remarks"></a>Poznámky

Tato metoda přidá kategorii s názvem *lpszName* do pole se **seznamem Příkazy.** Když uživatel vybere kategorii, příkazy zadané v *lstIDS* se zobrazí v seznamu příkazů.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Vytvoří `CMFCRibbonCustomizePropertyPage` objekt.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parametry

*pPruh*<br/>
[v] Ukazatel na ovládací prvek pásu karet, pro který lze přizpůsobit možnosti.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK

Calleld systémem, když uživatel klepne na **tlačítko OK** v dialogovém okně **Přizpůsobit.**

```
virtual void OnOK();
```

### <a name="remarks"></a>Poznámky

Výchozí implementace aplikuje volby vybrané v dialogovém okně **Přizpůsobit** na panel nástrojů Rychlý přístup.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
