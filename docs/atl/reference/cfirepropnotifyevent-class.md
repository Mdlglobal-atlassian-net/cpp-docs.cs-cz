---
title: Cfirepropnotifyevent – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88c816fecf71b94d25ac676f8169eeb26a2982fc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760214"
---
# <a name="cfirepropnotifyevent-class"></a>Cfirepropnotifyevent – třída

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

*pUnk*  
[in] Ukazatel `IUnknown` objektu odesílání oznámení.

*dispID*  
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

*pUnk*  
[in] Ukazatel `IUnknown` objektu odesílání oznámení.

*dispID*  
[in] Identifikátor vlastnosti Chystáte se změnit.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
