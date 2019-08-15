---
title: IPropertyNotifySinkCP – třída
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: 9838a48b078cbc59a5ae86669ad9f26792d9816e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495630"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP – třída

Tato třída zpřístupňuje rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) jako odchozí rozhraní na připojeném objektu.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IPropertyNotifySinkCP`odvozena z.

*CDV*<br/>
Třída, která spravuje připojení mezi spojovacím bodem a jeho jímkami. Výchozí hodnota je [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), která umožňuje neomezená připojení. Můžete také použít [CComUnkArray](../../atl/reference/ccomunkarray-class.md), který určuje pevný počet připojení.

## <a name="remarks"></a>Poznámky

`IPropertyNotifySinkCP`dědí všechny metody prostřednictvím své základní třídy, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

Rozhraní [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) umožňuje, aby objekt jímky přijímal oznámení o změnách vlastností. Třída `IPropertyNotifySinkCP` zpřístupňuje toto rozhraní jako odchozí rozhraní na připojeném objektu. Klient musí implementovat `IPropertyNotifySink` metody pro jímku.

Odvodit třídu z `IPropertyNotifySinkCP` , pokud chcete vytvořit bod připojení, který `IPropertyNotifySink` představuje rozhraní.

Další informace o použití bodů připojení v knihovně ATL najdete v článku [body připojení](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

## <a name="see-also"></a>Viz také:

[IConnectionPointImpl – třída](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl – třída](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
