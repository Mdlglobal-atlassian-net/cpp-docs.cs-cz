---
title: CFirePropNotifyEvent Class
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496942"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent Class

Tato třída poskytuje metody pro upozorňování jímky kontejneru týkající se změn vlastností ovládacího prvku.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|Tras Upozorní jímku kontejneru, že došlo ke změně vlastnosti ovládacího prvku.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|Tras Upozorní jímku kontejneru na změnu vlastnosti ovládacího prvku.|

## <a name="remarks"></a>Poznámky

`CFirePropNotifyEvent`má dvě metody, které oznamují jímku kontejneru, že došlo ke změně vlastnosti ovládacího prvku nebo se chystá změnit.

Pokud třída implementující váš ovládací prvek `IPropertyNotifySink`je odvozena z `CFirePropNotifyEvent` , metody jsou vyvolány při `FireOnChanged`volání `FireOnRequestEdit` nebo. Pokud vaše třída ovládacího prvku není odvozena `IPropertyNotifySink`od, volání těchto funkcí vrátí S_OK.

Další informace o vytváření ovládacích prvků naleznete v [kurzu ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

Upozorní všechna připojená rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (na každém bodu připojení objektu), že se změnila zadaná vlastnost objektu.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Ukazatel na `IUnknown` objekt, který odesílá oznámení.

*dispID*<br/>
pro Identifikátor vlastnosti, která se změnila.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je bezpečná pro volání, i když váš ovládací prvek nepodporuje spojovací body.

##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

Upozorní všechna připojená rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (na každém bodu připojení objektu), že se má změnit zadaná vlastnost objektu.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
pro Ukazatel na `IUnknown` objekt, který odesílá oznámení.

*dispID*<br/>
pro Identifikátor vlastnosti, kterou chcete změnit.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je bezpečná pro volání, i když váš ovládací prvek nepodporuje spojovací body.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
