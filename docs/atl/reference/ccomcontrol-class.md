---
title: Třída CComControl
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: 3518de3596748fa284c1f898b69d1576903e9510
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320771"
---
# <a name="ccomcontrol-class"></a>Třída CComControl

Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Třída implementující ovládací prvek.

*WinBase*<br/>
Základní třída, která implementuje funkce okna. Výchozí hodnota je [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Ccomcontrol::Ccomcontrol](#ccomcontrol)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CcomControl::Rozhraní controlquery](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Vytvoří okno pro ovládací prvek.|
|[CcomControl::FireOnChanged](#fireonchanged)|Upozorní jímky kontejneru, že došlo ke změně vlastnosti ovládacího prvku.|
|[Ccomcontrol::FireOnRequestEdit](#fireonrequestedit)|Upozorní jímky kontejneru, že vlastnost ovládacího prvku se chystá změnit a že objekt se ptá jímky, jak postupovat.|
|[CComControl::Okno se zprávou](#messagebox)|Volání této metody vytvořit, zobrazit a provozovat okno se zprávou.|

## <a name="remarks"></a>Poznámky

`CComControl`je sada užitečných funkcí pomocníka řízení a základních datových členů pro ovládací prvky ATL. Když vytvoříte standardní ovládací prvek nebo ovládací prvek DHTML pomocí Průvodce řízením `CComControl`atl, průvodce automaticky odvodí třídu z aplikace . `CComControl`odvozuje většinu svých metod z [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Další informace o vytvoření ovládacího prvku naleznete v [kurzu atl](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodci projektem atl naleznete v článku [Vytvoření projektu atl](../../atl/reference/creating-an-atl-project.md).

Ukázka metod `CComControl` a datových členů naleznete v ukázce [CIRC.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a>Ccomcontrol::Ccomcontrol

Konstruktor

```
CComControl();
```

### <a name="remarks"></a>Poznámky

Volá [konstruktor CComControlBase,](ccomcontrolbase-class.md#ccomcontrolbase) `m_hWnd` předávání datového člena zděděného prostřednictvím [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a>CcomControl::Rozhraní controlquery

Načte ukazatel na požadované rozhraní.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID požadovaného rozhraní.

*Ppv*<br/>
[out] Ukazatel rozhraní identifikovaný *iid*nebo NULL, pokud rozhraní není nalezeno.

### <a name="remarks"></a>Poznámky

Zpracovává pouze rozhraní v tabulce mapy COM.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComControl::CreateControlWindow

Ve výchozím nastavení vytvoří okno pro `CWindowImpl::Create`ovládací prvek voláním .

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[v] Popisovač do okna nadřazeného nebo vlastníka. Musí být zadáno platné popisovač okna. Ovládací okno je omezena na oblast nadřazeného okna.

*rcPos*<br/>
[v] Počáteční velikost a umístění okna, které má být vytvořeno.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu, pokud chcete udělat něco jiného, než vytvořit jedno okno, například vytvořit dvě okna, z nichž jeden se stane panel u nástrojů pro váš ovládací prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a>CcomControl::FireOnChanged

Upozorní jímky kontejneru, že došlo ke změně vlastnosti ovládacího prvku.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
[v] Identifikátor vlastnosti, která byla změněna.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud vaše třída ovládacího prvku pochází z [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), tato metoda volá [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) upozornit všechna připojená `IPropertyNotifySink` rozhraní, že zadaná vlastnost ovládacího prvku byla změněna. Pokud vaše třída ovládacího `IPropertyNotifySink`prvku není odvozena z , tato metoda vrátí S_OK.

Tato metoda je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a>Ccomcontrol::FireOnRequestEdit

Upozorní jímky kontejneru, že vlastnost ovládacího prvku se chystá změnit a že objekt se ptá jímky, jak postupovat.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
[v] Identifikátor vlastnosti, která se bude měnit.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud vaše třída ovládacího prvku pochází z [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), tato metoda volá [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) upozornit všechna připojená `IPropertyNotifySink` rozhraní, že zadaná vlastnost ovládacího prvku se chystá změnit. Pokud vaše třída ovládacího `IPropertyNotifySink`prvku není odvozena z , tato metoda vrátí S_OK.

Tato metoda je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a>CComControl::Okno se zprávou

Volání této metody vytvořit, zobrazit a provozovat okno se zprávou.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Text, který se má zobrazit v poli se zprávou.

*lpszTitulek*<br/>
Název dialogového okna. Pokud null (výchozí), je použit název "Chyba".

*nTyp*<br/>
Určuje obsah a chování dialogového okna. Seznam různých dostupných polí se zprávami naleznete v položce [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) v dokumentaci k sdksystému Windows SDK. Výchozí nastavení poskytuje jednoduché tlačítko **OK.**

### <a name="return-value"></a>Návratová hodnota

Vrátí celočíselnou hodnotu určující jednu z hodnot položek nabídky uvedených v poli [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) v dokumentaci k programu Windows SDK.

### <a name="remarks"></a>Poznámky

`MessageBox`je užitečné jak během vývoje, tak jako snadný způsob zobrazení chybové nebo varovné zprávy uživateli.

## <a name="see-also"></a>Viz také

[Třída CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CComControlBase](../../atl/reference/ccomcontrolbase-class.md)<br/>
[Třída CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)
