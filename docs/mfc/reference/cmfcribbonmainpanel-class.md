---
title: Cmfcribbonmainpanel – třída
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
ms.openlocfilehash: e4bd1ab8cffc87d5079518cf9a1d6e430ca40fd9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294440"
---
# <a name="cmfcribbonmainpanel-class"></a>Cmfcribbonmainpanel – třída

Implementuje panel pásu karet, který se zobrazí po kliknutí [cmfcribbonapplicationbutton –](../../mfc/reference/cmfcribbonapplicationbutton-class.md).

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Výchozí konstruktor.|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonMainPanel::Add](#add)|Přidá prvek pásu karet do levého podokna tlačítko panelu aplikací. (Přepíše [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|Přidá textový řetězec do nabídky seznam posledních souborů.|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|Přidá prvek pásu karet do dolní podokno panelu aplikace pásu karet.|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|Přidá prvek pásu karet do pravého podokna tlačítko panelu aplikací.|
|`CMFCRibbonMainPanel::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|Vrací obdélník, který představuje oblasti na hlavním panelu pásu karet.|
|`CMFCRibbonMainPanel::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|

## <a name="remarks"></a>Poznámky

Zobrazí rozhraní `CMFCRibbonMainPanel` při otevření panelu aplikací. Obsahuje tři podokna:

- Levé podokno obsahuje příkazy, které jsou spojené se soubory, třeba **otevřít**, **Uložit**, **tisk**, a **Zavřít**. Chcete-li přidat příkaz do tohoto podokna, zavolejte [CMFCRibbonMainPanel::Add](#add).

- Pravé podokno obsahuje možnosti, které mění příkaz, který klikněte v levém podokně. Vyberete-li například **uložit jako** v levém podokně, v pravém podokně můžete zobrazit dostupné typy souborů. Chcete-li přidat položku do tohoto podokna, zavolejte [CMFCRibbonMainPanel::AddToRight](#addtoright).

- Dolní podokno obsahuje tlačítka, která umožňují změnit nastavení aplikace a ukončit program. Chcete-li přidat položku do tohoto podokna, zavolejte [CMFCRibbonMainPanel::AddToBottom](#addtobottom).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonMainPanel.h

##  <a name="add"></a>  CMFCRibbonMainPanel::Add

Přidá prvek pásu karet do levého podokna tlačítko panelu aplikací.

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
[out v] Ukazatel na prvek pásu karet přidat na hlavním panelu.

### <a name="remarks"></a>Poznámky

Přidá prvek pásu karet na panelu. Elementy přidané pomocí této metody se nachází v levém sloupci na hlavním panelu.

##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList

Přidá textový řetězec do nabídky seznam posledních souborů.

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
Určuje řetězec pro přidání na seznam posledních souborů.

*nWidth*<br/>
Určuje šířku v pixelech, poslední panel seznamu souborů.

### <a name="remarks"></a>Poznámky

##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom

Přidá prvek pásu karet do dolní podokno panelu aplikace pásu karet.

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
[out v] Ukazatel na prvek pásu karet přidat k dolnímu okraji na hlavním panelu.

### <a name="remarks"></a>Poznámky

##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight

Přidá prvek pásu karet do pravého podokna tlačítko panelu aplikací.

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>Parametry

*pElem*<br/>
Ukazatel na prvek pásu karet přidán na pravé straně hlavního panelu.

*nWidth*<br/>
Určuje šířku v pixelech na pravém panelu.

### <a name="remarks"></a>Poznámky

Tuto funkci použijte, chcete-li přidat prvek pásu karet na pravém panelu. Pravý panel obvykle zobrazí seznam posledních souborů, ale můžete přidat libovolné další prvek pásu karet tady.

##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame

Vrací obdélník, který představuje oblasti na hlavním panelu pásu karet.

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>Návratová hodnota

Obdélník, který představuje oblasti na hlavním panelu pásu karet.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel – třída](../../mfc/reference/cmfcribbonpanel-class.md)
