---
title: Globální funkce kontextu zařízení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d85767ad529cb54686ff2cde186bd4a681d3570
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063312"
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

*hDC*<br/>
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

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)
