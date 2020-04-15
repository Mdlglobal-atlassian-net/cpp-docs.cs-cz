---
title: Makra stavu objektu
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 5617ce7fb972c98775072f72244f91052d41ece3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326169"
---
# <a name="object-status-macros"></a>Makra stavu objektu

Toto makro nastaví příznaky, které patří ovládacím prvkům ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Používá se v ovládacích prvcích ActiveX atl nastavit příznaky OLEMISC.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

Používá se v ovládacích prvcích ActiveX atl nastavit příznaky OLEMISC.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parametry

*chybový stav*<br/>
Všechny příslušné příznaky OLEMISC.

### <a name="remarks"></a>Poznámky

Toto makro slouží k nastavení příznaků OLEMISC pro ovládací prvek ActiveX. Další podrobnosti naleznete v [adrese IOleObject::GetMiscStatus.](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
