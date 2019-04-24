---
title: Makra stavu objektů
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: cb5ff6d7570b03b32852fc450f58043446f721f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198171"
---
# <a name="object-status-macros"></a>Makra stavu objektů

Toto makro nastaví příznaky, které patří ovládací prvky ActiveX.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Použít v ovládacích prvcích ActiveX knihovny ATL nastavit OLEMISC příznaky.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS

Použít v ovládacích prvcích ActiveX knihovny ATL nastavit OLEMISC příznaky.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parametry

*miscStatus*<br/>
Všechny použitelné OLEMISC příznaky.

### <a name="remarks"></a>Poznámky

Toto makro se používá k nastavení OLEMISC příznaky pro ovládací prvek ActiveX. Odkazovat na [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) další podrobnosti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Viz také:

[Makra](../../atl/reference/atl-macros.md)
