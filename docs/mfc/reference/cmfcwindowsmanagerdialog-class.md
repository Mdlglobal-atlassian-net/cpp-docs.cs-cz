---
title: CMFCWindowsManagerDialog Class
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 5089decc7a118cd867aa14df51f5d7e269221108
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767401"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog Class

`CMFCWindowsManagerDialog` Objektu umožňuje uživateli spravovat podřízená okna MDI v aplikaci MDI.

## <a name="syntax"></a>Syntaxe

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Vytvoří `CMFCWindowsManagerDialog` objektu.|

## <a name="remarks"></a>Poznámky

`CMFCWindowsManagerDialog` Obsahuje seznam podřízených oken MDI, které jsou právě otevřeny v aplikaci. Uživatele můžete ručně řídit stav podřízených oken MDI pomocí dialogovému oknu.

`CMFCWindowsManagerDialog` je vložena do [CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md). `CMFCWindowsManagerDialog` Se nejedná o třídu, která byste měli vytvořit ručně. Místo toho zavolejte funkci [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), potom vytvoří a zobrazí `CMFCWindowsManagerDialog` objektu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCWindowsManagerDialog` objektu voláním `CMDIFrameWndEx::ShowWindowsDialog`. Tento fragment kódu je součástí [Visual Studio demonstrační ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Vytvoří [cmfcwindowsmanagerdialog –](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objektu.

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parametry

*pMDIFrame*<br/>
[in] Ukazatel na okno nadřazené nebo vlastníka.

*bHelpButton*<br/>
[in] Parametr logické hodnoty, která určuje, zda se zobrazí rozhraní framework **pomáhají** tlačítko.

### <a name="remarks"></a>Poznámky

Další informace o vzhledu najdete v tématu [správce vizualizace](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx – třída](../../mfc/reference/cmdiframewndex-class.md)
