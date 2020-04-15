---
title: Globální funkce kontextu zařízení
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: e640f310a1976c29a39f0ab7c2575dfd1073c889
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330157"
---
# <a name="device-context-global-functions"></a>Globální funkce kontextu zařízení

Tato funkce vytvoří kontext zařízení pro dané zařízení.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Vytvoří kontext zařízení.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a>AtlCreateTargetDC

Vytvoří kontext zařízení pro zařízení zadané ve struktuře [DVTARGETDEVICE.](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
[v] Existující popisovač kontextu zařízení nebo NULL.

*Ptd*<br/>
[v] Ukazatel na `DVTARGETDEVICE` strukturu, která obsahuje informace o cílovém zařízení.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač do kontextu zařízení pro `DVTARGETDEVICE`zařízení určené v rozhraní . Pokud není zadáno žádné zařízení, vrátí popisovač na výchozí zobrazovací zařízení.

### <a name="remarks"></a>Poznámky

Pokud je struktura NULL a *hdc* je NULL, vytvoří kontext zařízení pro výchozí zobrazovací zařízení.

Pokud *hodnota HDC* není null a *hodnota PTD* je null, vrátí funkce existující *hodnotu HDC*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
