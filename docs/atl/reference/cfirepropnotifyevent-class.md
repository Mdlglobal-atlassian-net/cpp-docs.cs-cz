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
ms.openlocfilehash: 493bc00708d031f1bf7a4eb74d56e927a9c3f1dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245488"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent Class

Tato třída poskytuje metody pro oznámení kontejneru jímky týkající se změny vlastností ovládacího prvku.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statické) Upozorní kontejneru jímky, které se změnily vlastnosti ovládacího prvku.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statické) Upozorní jímky kontejneru, který vlastnosti ovládacího prvku se má změnit.|

## <a name="remarks"></a>Poznámky

`CFirePropNotifyEvent` má dvě metody, které oznámí jímky kontejneru, který došlo ke změně vlastnosti ovládacího prvku nebo se má změnit.

Pokud třída implementace ovládacího prvku je odvozena z `IPropertyNotifySink`, `CFirePropNotifyEvent` metody jsou vyvolány při volání `FireOnRequestEdit` nebo `FireOnChanged`. Pokud vaše třída ovládacího prvku není odvozen od `IPropertyNotifySink`, volání těchto funkcí vrátí hodnotu S_OK.

Další informace o vytváření ovládacích prvků naleznete v tématu [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged

Oznámí všechny připojené [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) rozhraní (v každém bodě připojení objektu), která je změněna vlastnost zadaného objektu.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel `IUnknown` objektu odesílání oznámení.

*dispID*<br/>
[in] Identifikátor vlastnosti, které se změnily.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit

Oznámí všechny připojené [ipropertynotifysink –](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) rozhraní (v každém bodě připojení objektu), které se zadaný objekt vlastnost se má změnit.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Ukazatel `IUnknown` objektu odesílání oznámení.

*dispID*<br/>
[in] Identifikátor vlastnosti Chystáte se změnit.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
