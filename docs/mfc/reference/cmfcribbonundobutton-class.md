---
title: Třída CMFCRibbonUndoButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
ms.openlocfilehash: f30e6f78b0988b791617ee0926cf649377972ce2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368802"
---
# <a name="cmfcribbonundobutton-class"></a>Třída CMFCRibbonUndoButton

Třída `CMFCRibbonUndoButton` implementuje rozevírací seznam tlačítko, které obsahuje nejnovější uživatelské příkazy. Uživatelé mohou vybrat jeden nebo více nejnovějších příkazů z rozevíracího seznamu a znovu je provést nebo vrátit.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Vytvoří nový `CMFCRibbonUndoButton` objekt pomocí zadaného ID příkazu, textového popisku a obrázků ze seznamu obrazů nadřazeného objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Přidá do seznamu akcí novou akci.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Vymaže seznam akcí, což je rozevírací seznam.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Určuje počet položek, které uživatel vybral z rozevíracího seznamu.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Označuje, zda objekt obsahuje nabídku.|

## <a name="remarks"></a>Poznámky

Třída `CMFCRibbonUndoButton` používá zásobník urestovnění rozevíracího seznamu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonUndoButton` třídy a přidat novou akci do seznamu akcí. Tento fragment kódu je součástí [ukázky miniaplikací na pásu karet](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CmFCRibbonGalerie](../../mfc/reference/cmfcribbongallery-class.md)

[Tlačítko ODsunul-pásCMFC](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonundobutton.h

## <a name="cmfcribbonundobuttonaddundoaction"></a><a name="addundoaction"></a>CMFCRibbonUndoButton::AddUndoAction

Přidá do seznamu akcí novou akci.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Popisek akce, který se zobrazí v rozevíracím seznamu.

## <a name="cmfcribbonundobuttoncleanupundolist"></a><a name="cleanupundolist"></a>CMFCRibbonUndoButton::CleanUpUndoList

Vymaže seznam akcí, což je rozevírací seznam.

```
void CleanUpUndoList();
```

## <a name="cmfcribbonundobuttoncmfcribbonundobutton"></a><a name="cmfcribbonundobutton"></a>CMFCRibbonUndoButton::CMFCRibbonUndoButton

Vytvoří nový `CMFCRibbonUndoButton` objekt pomocí zadaného ID příkazu, textového popisku a obrázků ze seznamu obrazů nadřazeného objektu.

```
CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex=-1,
    int nLargeImageIndex=-1);

CMFCRibbonUndoButton(
    UINT nID,
    LPCTSTR lpszText,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] Určuje identifikátor příkazu.

*lpszText*<br/>
[v] Určuje textový popisek tlačítka.

*nSmallImageIndex*<br/>
[v] Index založený na nule v seznamu obrázků nadřazeného objektu pro malý obrázek tlačítka.

*nLargeImageIndex*<br/>
[v] Index založený na nule v seznamu obrázků nadřazeného objektu pro velký obrázek tlačítka.

*hIkona*<br/>
[v] Úchyt k ikoně, kterou můžete použít jako obrázek tlačítka.

## <a name="cmfcribbonundobuttongetactionnumber"></a><a name="getactionnumber"></a>CMFCRibbonUndoButton::GetActionNumber

Určuje počet položek, které uživatel vybral z rozevíracího seznamu.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek, které uživatel vybral.

## <a name="cmfcribbonundobuttonhasmenu"></a><a name="hasmenu"></a>CMFCRibbonUndoButton::HasMenu

Označuje, zda objekt obsahuje nabídku.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery – třída](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
