---
title: Cmfcimageeditorpalettebar – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f36a9205cbaa2410dbdc25971a36879412f45ef0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398349"
---
# <a name="cmfcimageeditorpalettebar-class"></a>Cmfcimageeditorpalettebar – třída

Poskytuje funkce panel palety dialogovém okně editoru obrázků.

## <a name="syntax"></a>Syntaxe

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Vrátí výšku tlačítka na panelu nástrojů. (Přepíše [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Určuje, jestli můžou panelu nástrojů zobrazovat tlačítka, která jste rozšířili ohraničení. (Přepíše [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>Poznámky

Tato třída není určena pro použití přímo v kódu.

Rozhraní používá tuto třídu zobrazíte panel palety v dialogovém okně editoru obrázků. Další informace o dialogové okno editoru obrázků, naleznete v tématu [CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[Cmfctoolbar –](../../mfc/reference/cmfctoolbar-class.md)

[Cmfcimageeditorpalettebar –](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afximageeditordialog.h

##  <a name="getrowheight"></a>  CMFCImageEditorPaletteBar::GetRowHeight

Vrátí výšku tlačítka na panelu nástrojů.

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Výška každé tlačítko na panelu nástrojů.

##  <a name="isbuttonextrasizeavailable"></a>  CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable

Určuje, jestli můžou panelu nástrojů zobrazovat tlačítka, která jste rozšířili ohraničení.

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu FALSE.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog – třída](../../mfc/reference/cmfcimageeditordialog-class.md)
