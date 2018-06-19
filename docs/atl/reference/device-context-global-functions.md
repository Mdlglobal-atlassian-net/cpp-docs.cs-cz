---
title: Globální funkce kontextu zařízení | Microsoft Docs
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
ms.openlocfilehash: 37d54fbe9391cb53cca1d84401e90bb6fd47a479
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358586"
---
# <a name="device-context-global-functions"></a>Globální funkce kontextu zařízení
Tato funkce vytvoří kontext zařízení pro dané zařízení.  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|Vytvoří kontextu zařízení.|  
  
##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC  
 Vytvoří pro zadané zařízení v kontextu zařízení [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) struktura.  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>Parametry  
 *hDC*  
 [v] Existující popisovač kontextu zařízení, nebo **NULL**.  
  
 `ptd`  
 [v] Ukazatel **DVTARGETDEVICE** struktura, která obsahuje informace o cílové zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač do kontextu zařízení pro zařízení v zadané **DVTARGETDEVICE**. Pokud je zadána žádná zařízení, vrátí popisovač výchozí zobrazovací zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud strukturu **NULL** a *hdc* je **NULL**, vytvoří kontext zařízení pro výchozí zobrazení zařízení.  
  
 Pokud *hdc* není **NULL** a `ptd` je **NULL**, funkce vrátí hodnotu existující *hdc*.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
   
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
