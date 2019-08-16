---
title: Makra stavu objektu
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: dc50825d6b6e74dc263a097e86d8ea0d42989825
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495318"
---
# <a name="object-status-macros"></a>Makra stavu objektu

Toto makro nastaví příznaky, které patří ovládacím prvkům ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Používá se v ovládacích prvcích ATL ActiveX k nastavení příznaků OLEMISC.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

Používá se v ovládacích prvcích ATL ActiveX k nastavení příznaků OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parametry

*miscstatus*<br/>
Všechny použitelné příznaky OLEMISC

### <a name="remarks"></a>Poznámky

Toto makro slouží k nastavení příznaků OLEMISC pro ovládací prvek ActiveX. Další podrobnosti najdete v tématu [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Viz také:

[Makr](../../atl/reference/atl-macros.md)
