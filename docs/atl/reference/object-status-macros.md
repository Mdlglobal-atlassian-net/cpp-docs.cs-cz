---
title: Makra stavu objektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4b8be9cf1b421a66081fcf650462447d3c0ef7e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052535"
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

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
