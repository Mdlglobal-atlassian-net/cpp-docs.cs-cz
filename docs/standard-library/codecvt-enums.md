---
title: '&lt;výčty codecvt&gt;'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bbef1fe28c3321f06c0cc586062cd017168f8e73
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459795"
---
# <a name="ltcodecvtgt-enums"></a>&lt;výčty codecvt&gt;

## <a name="codecvt_mode"></a>Výčet codecvt_mode

Určuje informace o konfiguraci pro omezující vlastnosti [národního prostředí](../standard-library/locale-class.md) .

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Poznámky

Výčet definuje tři konstanty, které dodávají konfigurační informace do omezujících vlastností národního prostředí deklarované v [ \<codecvt >](../standard-library/codecvt.md). Jedinečné hodnoty jsou:

- `consume_header`, aby se při čtení vícebajtové sekvence využívala počáteční sekvence hlaviček, a určení endian pro následnou vícebajtovou sekvenci, která se má přečíst

- `generate_header`, pokud chcete vygenerovat počáteční sekvenci hlavičky při zápisu vícebajtové sekvence pro inzerování endian následné vícebajtové sekvence, která se má zapsat

- `little_endian`, aby se vygenerovala vícebajtová sekvence v pořadí s malým endianm, na rozdíl od výchozí objednávky big-endian

Tyto konstanty je možné ORed společně v libovolných kombinacích.

## <a name="see-also"></a>Viz také:

[\<codecvt>](../standard-library/codecvt.md)
