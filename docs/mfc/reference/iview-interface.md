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
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420818"
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
