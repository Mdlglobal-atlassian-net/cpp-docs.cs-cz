---
title: "Globální funkce kontextu zařízení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9aa685604580423262ab694d1285897cd29eef63
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="device-context-global-functions"></a>Globální funkce kontextu zařízení
Tato funkce vytvoří kontext zařízení pro dané zařízení.  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|Vytvoří kontextu zařízení.|  
  
##  <a name="atlcreatetargetdc"></a>AtlCreateTargetDC  
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
