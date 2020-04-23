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
ms.openlocfilehash: dfe77699a51ad2670c703d02e13e9062e76debcd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751279"
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
|[IView::OnActivateView](#onactivateview)|Volat knihovny MFC při aktivaci nebo deaktivaci zobrazení.|
|[IView::OnInitialUpdate](#oninitialupdate)|Volat rámci po zobrazení je nejprve připojen k dokumentu, ale před zobrazení je zpočátku zobrazena.|
|[IView::OnUpdate](#onupdate)|Volat knihovny MFC po změně dokumentu zobrazení; tato funkce umožňuje zobrazení aktualizovat jeho zobrazení tak, aby odráželo změny.|

## <a name="remarks"></a>Poznámky

`IView`implementuje několik `CWinFormsView` metod, které se používá k předávání oznámení společného zobrazení hostovanému spravovanému ovládacímu prvku. Jedná [se o OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) a [OnActivateView](#onactivateview).

`IView`je podobný [CView](../../mfc/reference/cview-class.md), ale používá se pouze se spravovanými zobrazeními a ovládacími prvky.

Další informace o používání formulářů Systému Windows naleznete [v tématu Použití ovládacího prvku uživatele formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Požadavky

Záhlaví: afxwinforms.h (definováno v sestavení atlmfc\lib\mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a>IView::OnActivateView

Volat knihovny MFC při aktivaci nebo deaktivaci zobrazení.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parametry

*aktivovat*<br/>
Označuje, zda je zobrazení aktivováno nebo deaktivováno.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::OnInitialUpdate

Volat rámci po zobrazení je nejprve připojen k dokumentu, ale před zobrazení je zpočátku zobrazena.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a>IView::OnUpdate

Volat knihovny MFC po změně dokumentu zobrazení.

```cpp
void OnUpdate();
```

## <a name="remarks"></a>Poznámky

Tato funkce umožňuje zobrazení aktualizovat jeho zobrazení tak, aby odrážely změny.

## <a name="see-also"></a>Viz také

[Třída CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)
