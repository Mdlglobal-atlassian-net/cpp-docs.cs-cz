---
title: '&lt;codecvt –&gt; výčty | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: 612570680bfacb2bc9c237c60b3e9f6c4f8266a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725332"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt –&gt; výčty

## <a name="codecvt_mode"></a>  codecvt_mode – výčet

Určuje konfigurační informace pro [národní prostředí](../standard-library/locale-class.md) omezujících vlastností.

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Poznámky

Výčet definuje tři konstanty, které poskytují informace o konfiguraci pro omezující vlastnosti národního prostředí, které jsou deklarované v [ \<codecvt – >](../standard-library/codecvt.md). Odlišné hodnoty jsou:

- `consume_header`, využívat sekvenci počáteční záhlaví při čtení vícebajtové sekvence a určit endianitou následné vícebajtové sekvence pro čtení

- `generate_header`, generovat sekvenci počáteční záhlaví při zápisu vícebajtové sekvence inzerovat endianitou následné vícebajtové sekvence má být zapsán

- `little_endian`, generovat vícebajtové pořadí podle little endian, na rozdíl od výchozí formát big-endian pořadí

Tyto konstanty může být sloučeny pomocí operátoru OR společně v libovolné kombinace.

## <a name="see-also"></a>Viz také:

[\<codecvt>](../standard-library/codecvt.md)<br/>
