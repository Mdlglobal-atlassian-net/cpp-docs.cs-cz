---
title: Globální funkce kontextu zařízení
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: aeebec65def9364e56156f6bb323815da012e11f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257435"
---
# <a name="device-context-global-functions"></a>Globální funkce kontextu zařízení

Tato funkce vytvoří kontext zařízení pro dané zařízení.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Vytvoří kontext zařízení.|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

Vytvoří kontext zařízení pro zařízení zadané ve [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) struktury.

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parametry

*hdc*<br/>
[in] Existující popisovač kontextu zařízení, nebo hodnota NULL.

*ptd*<br/>
[in] Ukazatel `DVTARGETDEVICE` strukturu, která obsahuje informace o cílové zařízení.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač kontext zařízení pro zařízení zadané ve `DVTARGETDEVICE`. Pokud není zadána žádná zařízení, vrátí popisovač na výchozím zobrazovacím zařízení.

### <a name="remarks"></a>Poznámky

Pokud struktura je NULL a *hdc* má hodnotu NULL, vytvoří kontext zařízení pro výchozím zobrazovacím zařízení.

Pokud *hdc* nemá hodnotu NULL a *ptd* má hodnotu NULL, funkce vrátí existující *hdc*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="see-also"></a>Viz také:

[Funkce](../../atl/reference/atl-functions.md)
