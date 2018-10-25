---
title: Cmfcribbonundobutton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 796337148247d5456b7e6223d79453e264834761
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076266"
---
# <a name="cmfcribbonundobutton-class"></a>Cmfcribbonundobutton – třída

`CMFCRibbonUndoButton` Třída implementuje tlačítko rozevíracího seznamu, který obsahuje nejnovější uživatelských příkazů. Uživatelé mohou vybrat jednu nebo více příkazů nejnovější z rozevíracího seznamu znovu, nebo je zrušit.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonUndoButton : public CMFCRibbonGallery
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Sestaví nový `CMFCRibbonUndoButton` s použitím ID příkazu, který zadáte, textový popisek a obrázků ze seznamu obrázků nadřazeného objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Přidá novou akci do seznamu akcí.|
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Vymaže seznam akcí, což je rozevíracím seznamu.|
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Určuje počet položek, které uživatel vybrat z rozevíracího seznamu.|
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Označuje, zda objekt obsahuje nabídku.|

## <a name="remarks"></a>Poznámky

`CMFCRibbonUndoButton` Třída používá k reprezentaci rozevíracího seznamu zásobníku.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonUndoButton` třídy a přidejte novou akci do seznamu akcí. Tento fragment kódu je součástí [miniaplikace na pásu karet ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md)

[Cmfcribbongallery –](../../mfc/reference/cmfcribbongallery-class.md)

[Cmfcribbonundobutton –](../../mfc/reference/cmfcribbonundobutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribbonundobutton.h

##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction

Přidá novou akci do seznamu akcí.

```
void AddUndoAction(LPCTSTR lpszLabel);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Popisek akce, která se zobrazí v rozevíracím seznamu.

##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList

Vymaže seznam akcí, což je rozevíracím seznamu.

```
void CleanUpUndoList();
```

##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton

Sestaví nový `CMFCRibbonUndoButton` s použitím ID příkazu, který zadáte, textový popisek a obrázků ze seznamu obrázků nadřazeného objektu.

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

*nID*<br/>
[in] Určuje identifikátor příkazu.

*lpszText*<br/>
[in] Určuje textový popisek tlačítka.

*nSmallImageIndex*<br/>
[in] Index založený na nule v seznamu obrázků nadřazeného objektu pro malý obrázek tlačítka.

*nLargeImageIndex*<br/>
[in] Index založený na nule v seznamu obrázků nadřazeného objektu pro velkých obrázku tlačítka.

*hIcon*<br/>
[in] Popisovač pro ikonu, která můžete použít jako obrázek tlačítka.

##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber

Určuje počet položek, které uživatel vybrat z rozevíracího seznamu.

```
int GetActionNumber() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek, které uživatel vybral.

##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu

Označuje, zda objekt obsahuje nabídku.

```
virtual BOOL HasMenu() const;
```

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery – třída](../../mfc/reference/cmfcribbongallery-class.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
