---
title: CComControl – třída
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
ms.openlocfilehash: bf0f64d8c7b8e8a3347e4c0fcad902b9e8a0ecb4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497523"
---
# <a name="ccomcontrol-class"></a>CComControl – třída

Tato třída poskytuje metody pro vytváření a správu ovládacích prvků ATL.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Třída, která implementuje ovládací prvek.

*WinBase*<br/>
Základní třída, která implementuje funkce okna. Výchozí hodnota je [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Vytvoří okno pro ovládací prvek.|
|[CComControl::FireOnChanged](#fireonchanged)|Upozorní jímku kontejneru, že došlo ke změně vlastnosti ovládacího prvku.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Upozorní jímku kontejneru, že se chystá Změna vlastnosti ovládacího prvku a zda objekt požaduje, aby bylo možné pokračovat v jímky.|
|[CComControl::MessageBox](#messagebox)|Voláním této metody můžete vytvořit, zobrazit a provozovat okno se zprávou.|

## <a name="remarks"></a>Poznámky

`CComControl`je sada užitečných pomocných funkcí ovládacího prvku a základních datových členů pro ovládací prvky ATL. Při vytváření standardního ovládacího prvku nebo ovládacího prvku DHTML pomocí Průvodce ovládacími prvky ATL bude průvodce automaticky odvozovat třídu z `CComControl`. `CComControl`odvodí většinu svých metod z [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Další informace o vytvoření ovládacího prvku naleznete v [kurzu ATL](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodci projektem ATL naleznete v článku [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

Ukázku `CComControl` metod a datových členů naleznete v ukázce [str](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="ccomcontrol"></a>CComControl::CComControl

Konstruktor

```
CComControl();
```

### <a name="remarks"></a>Poznámky

Volá konstruktor [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) , který `m_hWnd` předá datový člen zděděný prostřednictvím [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

Načte ukazatel na požadované rozhraní.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID požadovaného rozhraní

*ppv*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *identifikátorem IID*nebo hodnotu null, pokud rozhraní nebylo nalezeno.

### <a name="remarks"></a>Poznámky

Zpracovává pouze rozhraní v tabulce map modelu COM.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow

Ve výchozím nastavení vytvoří okno pro ovládací prvek voláním `CWindowImpl::Create`.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
pro Zařadit do nadřazeného nebo vlastníka okna. Musí být dodán platný popisovač okna. Okno ovládacího prvku je omezeno na oblast svého nadřazeného okna.

*rcPos*<br/>
pro Počáteční velikost a pozice okna, které má být vytvořeno.

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete udělat něco jiného než vytvořit jedno okno, například pro vytvoření dvou oken, z nichž jeden se změní na panel nástrojů pro váš ovládací prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>CComControl::FireOnChanged

Upozorní jímku kontejneru, že došlo ke změně vlastnosti ovládacího prvku.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*<br/>
pro Identifikátor vlastnosti, která se změnila.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je vaše třída ovládacího prvku odvozena z [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), tato metoda volá [CFirePropNotifyEvent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) , aby `IPropertyNotifySink` upozornila všechna připojená rozhraní, že se zadaná vlastnost ovládacího prvku změnila. Pokud vaše třída ovládacího prvku není odvozena `IPropertyNotifySink`z, tato metoda vrátí hodnotu S_OK.

Tato metoda je bezpečná pro volání, i když ovládací prvek nepodporuje spojovací body.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit

Upozorní jímku kontejneru, že se chystá Změna vlastnosti ovládacího prvku a zda objekt požaduje, aby bylo možné pokračovat v jímky.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*<br/>
pro Identifikátor vlastnosti, kterou chcete změnit.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je vaše třída ovládacího prvku odvozena z [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), tato metoda volá [CFirePropNotifyEvent:: FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) , aby `IPropertyNotifySink` upozornila všechna připojená rozhraní, která se chystá změnit určenou vlastnost ovládacího prvku. Pokud vaše třída ovládacího prvku není odvozena `IPropertyNotifySink`z, tato metoda vrátí hodnotu S_OK.

Tato metoda je bezpečná pro volání, i když ovládací prvek nepodporuje spojovací body.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>CComControl:: MessageBox

Voláním této metody můžete vytvořit, zobrazit a provozovat okno se zprávou.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Text, který se má zobrazit v okně se zprávou

*lpszCaption*<br/>
Název dialogového okna Pokud má hodnotu NULL (výchozí), použije se název "Chyba".

*nType*<br/>
Určuje obsah a chování dialogového okna. Seznam různých oken zpráv, která jsou k dispozici, najdete v části [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) v dokumentaci k Windows SDK. Výchozí nastavení poskytuje jednoduché tlačítko **OK** .

### <a name="return-value"></a>Návratová hodnota

Vrací celočíselnou hodnotu určující jednu z hodnot položek nabídky, které jsou uvedeny v části [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) v dokumentaci Windows SDK.

### <a name="remarks"></a>Poznámky

`MessageBox`je užitečné jak během vývoje, tak pomocí snadného způsobu zobrazení zprávy o chybě nebo upozornění pro uživatele.

## <a name="see-also"></a>Viz také:

[CWindowImpl – třída](../../atl/reference/cwindowimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CComControlBase – třída](../../atl/reference/ccomcontrolbase-class.md)<br/>
[CComCompositeControl – třída](../../atl/reference/ccomcompositecontrol-class.md)
