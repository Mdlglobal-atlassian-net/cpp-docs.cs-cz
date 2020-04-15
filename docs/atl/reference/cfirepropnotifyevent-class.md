---
title: Třída CFirePropNotifyEvent
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
ms.openlocfilehash: 1dfce42176341d74ffc7d9b42f856e71b17bf4f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326960"
---
# <a name="cfirepropnotifyevent-class"></a>Třída CFirePropNotifyEvent

Tato třída poskytuje metody pro upozornění jímky kontejneru o změně vlastností ovládacího prvku.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CfirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statické) Upozorní jímky kontejneru, že došlo ke změně vlastnosti ovládacího prvku.|
|[CfirePropNotifyEvent::fireonrequestedit](#fireonrequestedit)|(Statické) Upozorní jímky kontejneru, že vlastnost ovládacího prvku se chystá změnit.|

## <a name="remarks"></a>Poznámky

`CFirePropNotifyEvent`má dvě metody, které upozorňují jímky kontejneru, že vlastnost ovládacího prvku se změnila nebo se chystá změnit.

Pokud třída implementující ovládací prvek `IPropertyNotifySink`je `CFirePropNotifyEvent` odvozen z , metody `FireOnRequestEdit` `FireOnChanged`jsou vyvolány při volání nebo . Pokud vaše třída ovládacího `IPropertyNotifySink`prvku není odvozen a volání těchto funkcí vrátit S_OK.

Další informace o vytváření ovládacích prvků naleznete v [kurzu atl](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CfirePropNotifyEvent::FireOnChanged

Upozorní všechna připojená rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (v každém spojovacím bodě objektu), že se změnila vlastnost zadaného objektu.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Ukazatel na `IUnknown` objekt odesílající oznámení.

*Dispid*<br/>
[v] Identifikátor vlastnosti, která byla změněna.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CfirePropNotifyEvent::fireonrequestedit

Upozorní všechna připojená rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) (v každém spojovacím bodě objektu), že se zadaný objekt změní.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[v] Ukazatel na `IUnknown` objekt odesílající oznámení.

*Dispid*<br/>
[v] Identifikátor vlastnosti, která se bude měnit.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je bezpečné volat i v případě, že ovládací prvek nepodporuje spojovací body.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
