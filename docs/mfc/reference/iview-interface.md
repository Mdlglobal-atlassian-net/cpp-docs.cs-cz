---
title: IView – rozhraní
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 7684ef034acd247355b3f572c86fcb80cb126b0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594347"
---
# <a name="iview-interface"></a>IView – rozhraní

Implementuje několik metod, které [CWinFormsView](../../mfc/reference/cwinformsview-class.md) používá k odesílání oznámení zobrazení spravovatelného ovládacího prvku.

## <a name="syntax"></a>Syntaxe

```
interface class IView
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Volá se v prostředí MFC, když se aktivuje nebo deaktivuje zobrazení.|
|[IView::OnInitialUpdate](#oninitialupdate)|Volá se rozhraním po zobrazení je nejprve připojen k dokumentu, ale před začátku zobrazení.|
|[IView::OnUpdate](#onupdate)|Volá se v prostředí MFC po byl změněn zobrazení dokumentu; Tato funkce umožňuje zobrazení aktualizovat zobrazení tak, aby odrážely změny.|

## <a name="remarks"></a>Poznámky

`IView` implementuje několik metod, které `CWinFormsView` používá k předávání běžné zobrazení oznámení na hostované spravovatelného ovládacího prvku. Jedná se o [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) a [OnActivateView](#onactivateview).

`IView` je podobný [CView](../../mfc/reference/cview-class.md), ale používá se pouze s ovládacími prvky a spravované zobrazení.

Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Požadavky

Záhlaví: afxwinforms.h (definované v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a> IView::OnActivateView

Volá se v prostředí MFC, když se aktivuje nebo deaktivuje zobrazení.
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parametry

*Aktivovat*<br/>
Určuje, zda je zobrazení se aktivuje nebo deaktivuje.

## <a name="oninitialupdate"></a> IView::OnInitialUpdate

Volá se rozhraním po zobrazení je nejprve připojen k dokumentu, ale před začátku zobrazení.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate

Volá se v prostředí MFC po dokumentu v zobrazení se změnila.
```
void OnUpdate();
```

## <a name="remarks"></a>Poznámky

Tato funkce umožňuje zobrazení aktualizovat zobrazení tak, aby odrážely změny.

## <a name="see-also"></a>Viz také

[CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)
