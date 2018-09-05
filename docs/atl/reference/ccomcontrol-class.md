---
title: Ccomcontrol – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
dev_langs:
- C++
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bc4004be27a057c96d9c10e7e7f261d8a5ddebe
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761349"
---
# <a name="ccomcontrol-class"></a>Ccomcontrol – třída

Tato třída poskytuje metody pro vytváření a správu ATL – ovládací prvky.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class WinBase = CWindowImpl<T>>  
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parametry

*T*  
Třída implementace ovládacího prvku.

*WinBase*  
Základní třída, která implementuje okny. Výchozí hodnota je [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Vytvoří okno pro ovládací prvek.|
|[CComControl::FireOnChanged](#fireonchanged)|Upozorní kontejneru jímky, které se změnily vlastnosti ovládacího prvku.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Kontejneru jímky upozorní, že ve vlastnosti ovládacího prvku se chystá změna a že objekt žádá jímka jak pokračovat dál.|
|[CComControl::MessageBox](#messagebox)|Voláním této metody lze vytvořit, zobrazit a pracovat okno se zprávou.|

## <a name="remarks"></a>Poznámky

`CComControl` je sada užitečných ovládací prvek pomocné funkce a základní datové členy pro ATL – ovládací prvky. Při vytváření standardního ovládacího prvku nebo ovládací prvek DHTML pomocí Průvodce ovládacími prvky ATL, průvodce automaticky odvodit třídu z `CComControl`. `CComControl` je odvozen většinu jeho metody ze [CComControlBase –](../../atl/reference/ccomcontrolbase-class.md).

Další informace o vytvoření ovládacího prvku, naleznete v tématu [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md). Další informace o Průvodce projektem ATL naleznete v článku [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md).

Pro ukázku `CComControl` metody a datové členy, najdete v článku [KR](../../visual-cpp-samples.md) vzorku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="ccomcontrol"></a>  CComControl::CComControl

Konstruktor

```
CComControl();
```

### <a name="remarks"></a>Poznámky

Volání [CComControlBase –](ccomcontrolbase-class.md#ccomcontrolbase) konstruktoru, předá `m_hWnd` datový člen zděděné z [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

Načte ukazatel na požadované rozhraní.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parametry

*identifikátor IID*  
[in] Identifikátor GUID se požadované rozhraní.

*ppv*  
[out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*, nebo hodnota NULL, pokud se nenajde rozhraní.

### <a name="remarks"></a>Poznámky

zpracovává pouze v tabulce mapy modelu COM rozhraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow

Ve výchozím nastavení, vytvoří okno pro ovládací prvek voláním `CWindowImpl::Create`.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*  
[in] Popisovač okna nadřazené nebo vlastníka. Je potřeba zadat popisovač okna platný. Okno ovládacího prvku je omezena na oblasti nezašle nadřazenému oknu.

*rcPos*  
[in] Počáteční velikost a umístění okna, který se má vytvořit.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu, pokud budete chtít udělat něco jiného než vytvořte jedno okno, například dvě okna vytvoříte, jedním z nich stane nástrojů pro ovládací prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>  CComControl::FireOnChanged

Upozorní kontejneru jímky, které se změnily vlastnosti ovládacího prvku.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*  
[in] Identifikátor vlastnosti, které se změnily.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je odvozena z třídy vašeho ovládacího prvku [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), tato metoda volá [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) upozornit všechny připojené `IPropertyNotifySink` rozhraní, které zadaný ovládací prvek Vlastnost se změnila. Pokud vaše třída ovládacího prvku není odvozen od `IPropertyNotifySink`, tato metoda vrátí hodnotu S_OK.

Tato metoda je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

Kontejneru jímky upozorní, že ve vlastnosti ovládacího prvku se chystá změna a že objekt žádá jímka jak pokračovat dál.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*  
[in] Identifikátor vlastnosti Chystáte se změnit.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je odvozena z třídy vašeho ovládacího prvku [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), tato metoda volá [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) upozornit všechny připojené `IPropertyNotifySink` rozhraní, které zadaný vlastnosti ovládacího prvku je změnit. Pokud vaše třída ovládacího prvku není odvozen od `IPropertyNotifySink`, tato metoda vrátí hodnotu S_OK.  

Tato metoda je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>  CComControl::MessageBox

Voláním této metody lze vytvořit, zobrazit a pracovat okno se zprávou.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parametry

*lpszText*  
Text, který se má zobrazit v okně se zprávou.

*lpszCaption*  
Pole Název dialogového okna. Pokud hodnotu NULL (výchozí), název se používá "Chyba".

*nTyp*  
Určuje obsah a chování dialogového okna. Zobrazit [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) položku v dokumentaci Windows SDK pro seznam k dispozici různé zprávami. Výchozí hodnota poskytuje jednoduchý **OK** tlačítko.

### <a name="return-value"></a>Návratová hodnota

Vrátí celočíselnou hodnotu určující jednu z hodnot položky nabídky v části [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) v dokumentaci Windows SDK.

### <a name="remarks"></a>Poznámky

`MessageBox` je užitečné při vývoji i snadný způsob, jak zobrazit chybu nebo upozornění pro uživatele.

## <a name="see-also"></a>Viz také

[Cwindowimpl – třída](../../atl/reference/cwindowimpl-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)   
[CComControlBase – třída](../../atl/reference/ccomcontrolbase-class.md)   
[CComCompositeControl – třída](../../atl/reference/ccomcompositecontrol-class.md)
