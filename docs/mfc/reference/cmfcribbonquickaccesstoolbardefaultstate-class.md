---
title: CMFCRibbonQuickAccessToolBarDefaultState – třída
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
ms.openlocfilehash: eb6b36066f34036ae599a94f4d1c07b2c633e730
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753522"
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState – třída

Pomocná třída, která spravuje výchozí stav panelu nástrojů Rychlý přístup, který je umístěn na panelu pásu karet ( [třída CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)).

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonQuickAccessToolBarDefaultState
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonQuickAccessToolBarDefaultState:::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Vytvoří `CMFCRibbonQuickAccessToolbarDefaultState` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Přidá příkaz do výchozího stavu panelu nástrojů Rychlý přístup. Tím se nezmění samotný panel nástrojů.|
|[CMFCRibbonRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Zkopíruje vlastnosti jednoho panelu nástrojů Rychlý přístup do jiného.|
|[CMFCRibbonRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Odebere všechny příkazy z panelu nástrojů Rychlý přístup. Tím se nezmění samotný panel nástrojů.|

## <a name="remarks"></a>Poznámky

Po vytvoření panelu nástrojů Rychlý přístup v aplikaci doporučujeme nastavit jeho výchozí stav voláním [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Tento výchozí stav se obnoví, když uživatel klepne na tlačítko **Obnovit** na stránce **Přizpůsobit** dialogovéokno **Možnosti** aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCRibbonRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonQuickAccessToolbarDefaultState` třídy a jak přidat příkaz do výchozího stavu panelu nástrojů Rychlý přístup.

[!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonquickaccesstoolbar.h

## <a name="cmfcribbonquickaccesstoolbardefaultstateaddcommand"></a><a name="addcommand"></a>CMFCRibbonRibbonQuickAccessToolBarDefaultState::AddCommand

Přidá příkaz do výchozího stavu panelu nástrojů Rychlý přístup.

```cpp
void AddCommand(
    UINT uiCmd,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parametry

*[v] uiCmd*<br/>
Určuje ID příkazu.

*[in] bIsVisible*<br/>
Nastaví viditelnost příkazu, když je panel nástrojů Rychlý přístup ve výchozím stavu.

### <a name="remarks"></a>Poznámky

Přidání příkazu do CMFCRibbonQuickAccessToolBarDefaultState dosáhne tři výsledky. Nejprve je každý přidaný příkaz uveden v rozevíracím seznamu na pravé straně panelu nástrojů Rychlý přístup. Tímto způsobem může uživatel tento příkaz snadno přidat nebo odebrat z panelu nástrojů Rychlý přístup. Za druhé, panel nástrojů Rychlý přístup se resetuje tak, aby zobrazoval pouze ty příkazy, které jsou uvedeny jako viditelné ve výchozím stavu, když uživatel klepne na tlačítko **Obnovit** v dialogovém okně **Přizpůsobit.** Za třetí, pokud jste nevolali [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), panel nástrojů Rychlý přístup používá viditelné příkazy z tohoto seznamu jako výchozí viditelné příkazy při prvním spuštění aplikace uživatelem. Po přidání všech požadovaných příkazů zavolejte [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) a nastavte tuto instanci jako výchozí stav panelu nástrojů Rychlý přístup na tomto panelu pásu karet.

## <a name="cmfcribbonquickaccesstoolbardefaultstatecopyfrom"></a><a name="copyfrom"></a>CMFCRibbonRibbonQuickAccessToolBarDefaultState::CopyFrom

Zkopíruje vlastnosti jednoho panelu nástrojů Rychlý přístup do jiného.

```cpp
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[v] Odkaz na zdrojový `CMFCRibbonQuickAccessToolBarDefaultState` objekt, ze který chcete kopírovat.

### <a name="remarks"></a>Poznámky

Tato metoda zkopíruje každý `CMFCRibbonQuickAccessToolBarDefaultState` příkaz ze zdrojového objektu do tohoto objektu pomocí metody [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand.](#addcommand)

## <a name="cmfcribbonquickaccesstoolbardefaultstatecmfcribbonquickaccesstoolbardefaultstate"></a><a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonRibbonQuickAccessToolBarDefaultState:::CMFCRibbonQuickAccessToolBarDefaultState

Vytvoří výchozí objekt stavu panelu nástrojů Rychlý přístup.

```
CMFCRibbonQuickAccessToolBarDefaultState();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je seznam příkazů, které nová instance [CMFRibbonQuickAccessToolDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) obsahuje, prázdný.

## <a name="cmfcribbonquickaccesstoolbardefaultstateremoveall"></a><a name="removeall"></a>CMFCRibbonRibbonQuickAccessToolBarDefaultState::RemoveAll

Vymaže seznam výchozích příkazů na panelu nástrojů Rychlý přístup.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Poznámky

Tato funkce odebere z této instance všechny příkazy, které předchozí volání [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) přidána.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
