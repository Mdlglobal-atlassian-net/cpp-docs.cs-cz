---
title: Cmfcribbonquickaccesstoolbardefaultstate – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
ms.openlocfilehash: 0ea9ec8de0b657fa4e7c601f9c3e676f550defa9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302478"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>Cmfcribbonquickaccesstoolbardefaultstate – třída

Pomocná třída, která spravuje výchozího stavu pro panel nástrojů Rychlý přístup, který je umístěn na pásu karet ( [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)).

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Vytvoří `CMFCRibbonQuickAccessToolbarDefaultState` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Přidá příkaz do výchozího stavu pro panel nástrojů Rychlý přístup. Nezmění se samotný panel nástrojů.|
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Kopíruje vlastnosti z jednoho panelu nástrojů Rychlý přístup do jiného.|
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Odebere všechny příkazy z panelu nástrojů Rychlý přístup. Nezmění se samotný panel nástrojů.|

## <a name="remarks"></a>Poznámky

Po vytvoření panelu nástrojů Rychlý přístup ve vaší aplikaci, doporučujeme nastavit výchozího stavu voláním [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Tato výchozí stav se obnoví, když uživatel klikne **resetování** tlačítko **vlastní** stránky vaší aplikace **možnosti** dialogové okno.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonQuickAccessToolbarDefaultState` třídy a tom, jak přidat příkaz do výchozího stavu pro panel nástrojů Rychlý přístup.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonquickaccesstoolbar.h

##  <a name="addcommand"></a>  CMFCRibbonQuickAccessToolBarDefaultState::AddCommand

Přidá příkaz do výchozího stavu pro panel nástrojů Rychlý přístup.

```
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*[in] uiCmd*<br/>
Určuje ID příkazu.

*[in] bIsVisible*<br/>
Nastaví, zda se příkaz panelu nástrojů Rychlý přístup je ve výchozím stavu.

### <a name="remarks"></a>Poznámky

Přidání příkazu cmfcribbonquickaccesstoolbardefaultstate – provede tři výsledky. Každé přidání příkazu je nejprve uvedená na rozevírací nabídku na pravé straně panelu nástrojů Rychlý přístup. Tímto způsobem můžete uživatele snadno přidat nebo odebrat tento příkaz z panelu nástrojů Rychlý přístup. Za druhé, je obnovit zobrazit pouze příkazy, které jsou uvedeny jako viditelný ve výchozím stavu po kliknutí na panel nástrojů Rychlý přístup **resetování** tlačítko **vlastní** dialogové okno. Třetí, pokud nebyla volána [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), panel nástrojů Rychlý přístup používá viditelné příkazy z tohoto seznamu jako výchozí viditelné příkazy při prvním spuštění aplikace uživatelem. Po přidání všech příkazů, které chcete volat [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) nastavení této instance jako výchozího stavu pro panel nástrojů Rychlý přístup z tento panel pásu karet.

##  <a name="copyfrom"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom

Kopíruje vlastnosti z jednoho panelu nástrojů Rychlý přístup do jiného.

```
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] Odkaz na zdroj `CMFCRibbonQuickAccessToolBarDefaultState` objektu, který chcete kopírovat.

### <a name="remarks"></a>Poznámky

Tato metoda zkopíruje každý příkaz ze zdroje `CMFCRibbonQuickAccessToolBarDefaultState` do tohoto objektu pomocí [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) metody.

##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>  CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState

Vytvoří výchozí objekt stav panelu nástrojů Rychlý přístup.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, seznam příkazů, které novou instanci [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) obsahuje je prázdný.

##  <a name="removeall"></a>  CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll

Vymaže seznam výchozích příkazů v panelu nástrojů Rychlý přístup.

```
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Tato funkce se odebere z této instance všechny příkazy, které předchozí volání [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) přidán.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
