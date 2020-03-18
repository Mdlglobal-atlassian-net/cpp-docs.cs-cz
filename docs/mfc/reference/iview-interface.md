---
title: Rozhraní IView
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
ms.openlocfilehash: e8afa7a5f5a7692f88ace4da08209b80f902b603
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445675"
---
# <a name="iview-interface"></a>Rozhraní IView

Implementuje několik metod, které [CWinFormsView](../../mfc/reference/cwinformsview-class.md) používá k odesílání oznámení zobrazení spravovanému ovládacímu prvku.

## <a name="syntax"></a>Syntaxe

```
interface class IView
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IView:: OnActivateView](#onactivateview)|Volá se knihovnou MFC při aktivaci nebo deaktivaci zobrazení.|
|[IView:: OnInitialUpdate](#oninitialupdate)|Volá se rozhraním po prvním připojení zobrazení k dokumentu, ale před tím, než se zobrazení zpočátku zobrazí.|
|[IView:: inupdate](#onupdate)|Volá se knihovnou MFC po úpravě dokumentu zobrazení; Tato funkce umožňuje zobrazení aktualizovat zobrazení tak, aby odráželo úpravy.|

## <a name="remarks"></a>Poznámky

`IView` implementuje několik metod, které `CWinFormsView` používá pro přeposílání běžných oznámení o zobrazení do hostovaného spravovaného ovládacího prvku. Jsou to [OnInitialUpdate](#oninitialupdate), [Update](#onupdate) a [OnActivateView](#onactivateview).

`IView` je podobná jako [CView](../../mfc/reference/cview-class.md), ale používá se pouze se spravovanými zobrazeními a ovládacími prvky.

Další informace o použití model Windows Forms naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Požadavky

Záhlaví: afxwinforms. h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a>IView:: OnActivateView

Volá se knihovnou MFC při aktivaci nebo deaktivaci zobrazení.

```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parametry

*aktivovat*<br/>
Označuje, zda se zobrazení aktivuje nebo deaktivuje.

## <a name="oninitialupdate"></a>IView:: OnInitialUpdate

Volá se rozhraním po prvním připojení zobrazení k dokumentu, ale před tím, než se zobrazení zpočátku zobrazí.

```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView:: inupdate

Volá se knihovnou MFC po úpravě dokumentu zobrazení.

```
void OnUpdate();
```

## <a name="remarks"></a>Poznámky

Tato funkce umožňuje zobrazení aktualizovat zobrazení tak, aby odráželo úpravy.

## <a name="see-also"></a>Viz také

[CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)
