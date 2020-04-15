---
title: CMFCWindowsManagerDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: e3928c0d3ae4f607dceb99c0762277e8ea9ddbde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319830"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog – třída

Objekt `CMFCWindowsManagerDialog` umožňuje uživateli spravovat podřízená okna MDI v aplikaci MDI.

## <a name="syntax"></a>Syntaxe

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Vytvoří `CMFCWindowsManagerDialog` objekt.|

## <a name="remarks"></a>Poznámky

Obsahuje `CMFCWindowsManagerDialog` seznam podřízených oken MDI, které jsou aktuálně otevřeny v aplikaci. Uživatel může ručně řídit stav podřízených oken MDI pomocí tohoto dialogového okna.

`CMFCWindowsManagerDialog`je vložena do [třídy CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md). Není `CMFCWindowsManagerDialog` třída, kterou byste měli vytvořit ručně. Místo toho volání funkce [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), a `CMFCWindowsManagerDialog` vytvoří a zobrazí objekt.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCWindowsManagerDialog` vytvořit objekt `CMDIFrameWndEx::ShowWindowsDialog`voláním . Tento fragment kódu je součástí [ukázky ukázky aplikace Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxWindowsManagerDialog.h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Vytvoří objekt [CMFCWindowsManagerDialog.](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parametry

*pMDIFrame*<br/>
[v] Ukazatel na nadřazené nebo vlastníkřové okno.

*bTlačítko nápovědy*<br/>
[v] Logický parametr, který určuje, zda se v rámci zobrazí tlačítko **nápovědy.**

### <a name="remarks"></a>Poznámky

Další informace o vizuálních manažerech naleznete v tématu [Visualization Manager](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)
