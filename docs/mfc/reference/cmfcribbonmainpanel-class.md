---
title: Třída CMFCRibbonMainPanel
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: 1458039c25f2379b3c3db553b2010e9391df28db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375096"
---
# <a name="cmfcribbonmainpanel-class"></a>Třída CMFCRibbonMainPanel

Implementuje panel pásu karet, který se zobrazí po klepnutí na [tlačítko CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Výchozí konstruktor.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonMainPanel::Přidat](#add)|Přidá prvek pásu karet do levého podokna panelu tlačítka aplikace. (Přepíše [CMFCRibbonPanel::Přidat](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Přidá textový řetězec do nabídky seznamu posledních souborů.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Přidá prvek pásu karet do spodního podokna panelu aplikace pásu karet.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Přidá prvek pásu karet do pravého podokna panelu tlačítka aplikace.|
|`CMFCRibbonMainPanel::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Vrátí obdélník, který představuje oblast hlavního panelu pásu karet.|
|`CMFCRibbonMainPanel::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|

## <a name="remarks"></a>Poznámky

Rámec zobrazí `CMFCRibbonMainPanel` při otevření panelu aplikace. Obsahuje tři tabule:

- Levé podokno obsahuje příkazy přidružené k souborům, například **Otevřít**, **Uložit**, **Tisknout**a **Zavřít**. Chcete-li do tohoto podokna přidat příkaz, zavolejte [CMFCRibbonMainPanel::Add](#add).

- Pravé podokno obsahuje možnosti, které upravují příkaz, na který klepnete v levém podokně. Pokud například klepnete na tlačítko **Uložit jako** v levém podokně, může pravé podokno zobrazit dostupné typy souborů. Chcete-li přidat položku do tohoto podokna, zavolejte [CMFCRibbonMainPanel::AddToRight](#addtoright).

- Dolní podokno obsahuje tlačítka, která umožňují změnit nastavení aplikace a ukončit program. Chcete-li přidat položku do tohoto podokna, zavolejte [CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFCFCPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonHlavnípanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonMainPanel.h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a>CMFCRibbonMainPanel::Přidat

Přidá prvek pásu karet do levého podokna panelu tlačítka aplikace.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
[dovnitř, ven] Ukazatel na prvek pásu karet, který chcete přidat do hlavního panelu.

### <a name="remarks"></a>Poznámky

Přidá do panelu prvek pásu karet. Prvky přidané touto metodou budou umístěny v levém sloupci hlavního panelu.

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList

Přidá textový řetězec do nabídky seznamu posledních souborů.

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
Určuje řetězec, který má být připojován do seznamu posledních souborů.

*nŠířka*<br/>
Určuje šířku panelu seznamu posledních souborů v obrazových bodech.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom

Přidá prvek pásu karet do spodního podokna panelu aplikace pásu karet.

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
[dovnitř, ven] Ukazatel na prvek pásu karet, který chcete přidat do dolní části hlavního panelu.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight

Přidá prvek pásu karet do pravého podokna panelu tlačítka aplikace.

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
Ukazatel na prvek pásu karet, který má být přidán na pravou stranu hlavního panelu.

*nŠířka*<br/>
Určuje šířku pravého panelu v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k přidání prvku pásu karet do pravého panelu. Pravý panel obvykle zobrazuje seznam posledních souborů, ale zde můžete přidat jakýkoli další prvek pásu karet.

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame

Vrátí obdélník, který představuje oblast hlavního panelu pásu karet.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Návratová hodnota

Obdélník, který představuje oblast hlavního panelu pásu karet.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel – třída](../../mfc/reference/cmfcribbonpanel-class.md)
