---
title: Globální funkce kontextu zařízení
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d225bd0cd996fd908479b5a93aad81ea0428900b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496091"
---
# <a name="device-context-global-functions"></a>Globální funkce kontextu zařízení

Tato funkce vytvoří kontext zařízení pro dané zařízení.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Vytvoří kontext zařízení.|

##  <a name="atlcreatetargetdc"></a>AtlCreateTargetDC

Vytvoří kontext zařízení pro zařízení zadané ve struktuře [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) .

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parametry

*hdc*<br/>
pro Stávající popisovač kontextu zařízení nebo hodnota NULL.

*ptd*<br/>
pro Ukazatel na `DVTARGETDEVICE` strukturu, která obsahuje informace o cílovém zařízení.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač kontextu zařízení určeného v `DVTARGETDEVICE`. Pokud není zadáno žádné zařízení, vrátí popisovač výchozí zobrazovací zařízení.

### <a name="remarks"></a>Poznámky

Pokud má struktura hodnotu NULL a *HDC* má hodnotu null, vytvoří kontext zařízení pro výchozí zobrazovací zařízení.

Pokud *HDC* není null a *PTD* je null, funkce vrátí existující *HDC*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

## <a name="see-also"></a>Viz také:

[Funkce](../../atl/reference/atl-functions.md)
