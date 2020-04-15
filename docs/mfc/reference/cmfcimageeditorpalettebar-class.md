---
title: CMFCImageEditorPaletteBar – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
ms.openlocfilehash: 33d4bc0c72718d028031ac11bc67da6aec5e4907
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374430"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar – třída

Poskytuje funkci panelu palety dialogovému oknu editoru obrázků.

## <a name="syntax"></a>Syntaxe

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Vrátí výšku tlačítek panelu nástrojů. (Přepíše [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCImageEditorPaletteBar::isbuttonextrasizeK dispozici](#isbuttonextrasizeavailable)|Určuje, zda lze na panelu nástrojů zobrazovat tlačítka s rozšířenými ohraničeními. (Přepíše [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>Poznámky

Tato třída není určena pro použití přímo z vašeho kódu.

Rozhraní framework používá tuto třídu k zobrazení panelu palet y v dialogovém okně editoru obrázků. Další informace o dialogovém okně editoru obrázků naleznete v tématu [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCPanel](../../mfc/reference/cmfctoolbar-class.md)

[CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afximageeditordialog.h

## <a name="cmfcimageeditorpalettebargetrowheight"></a><a name="getrowheight"></a>CMFCImageEditorPaletteBar::GetRowHeight

Vrátí výšku tlačítek panelu nástrojů.

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Výška každého tlačítka na panelu nástrojů.

## <a name="cmfcimageeditorpalettebarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCImageEditorPaletteBar::isbuttonextrasizeK dispozici

Určuje, zda lze na panelu nástrojů zobrazovat tlačítka s rozšířenými ohraničeními.

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu FALSE.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
