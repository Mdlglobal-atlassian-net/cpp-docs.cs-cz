---
title: výčty &lt;codecvt&gt;
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bbef1fe28c3321f06c0cc586062cd017168f8e73
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421924"
---
# <a name="ltcodecvtgt-enums"></a>výčty &lt;codecvt&gt;

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

Výčet definuje tři konstanty, které dodávají konfigurační informace do omezujících vlastností národního prostředí deklarované v [\<codecvt >](../standard-library/codecvt.md). Jedinečné hodnoty jsou:

- `consume_header`pro použití počáteční sekvence hlavičky při čtení vícebajtové sekvence a určení endian pro následnou vícebajtovou sekvenci, která se má přečíst

- `generate_header`pro vygenerování počáteční sekvence hlavičky při zápisu vícebajtové sekvence pro inzerování endian následné vícebajtové sekvence, která se má zapsat

- `little_endian`, aby se vygenerovala vícebajtová sekvence v řádu Little-endian, na rozdíl od výchozí objednávky big-endian

Tyto konstanty je možné ORed společně v libovolných kombinacích.

## <a name="see-also"></a>Viz také

[\<codecvt >](../standard-library/codecvt.md)
