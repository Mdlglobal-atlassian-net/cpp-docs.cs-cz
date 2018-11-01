---
title: '&lt;codecvt –&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: 0b43c7c148076e96dd0d3f444ffa8b6bad7c8b29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566150"
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
