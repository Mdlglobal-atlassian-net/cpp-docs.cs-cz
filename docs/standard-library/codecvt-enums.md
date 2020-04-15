---
title: '&lt;kodekové&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: e67290d8de0b8251191c4a93b66b7e19a293ed61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371943"
---
# <a name="ltcodecvtgt-enums"></a>&lt;kodekové&gt; výčty

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a>codecvt_mode výčet

Určuje informace o konfiguraci pro omezující [vlastnosti národního prostředí.](../standard-library/locale-class.md)

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Poznámky

Výčet definuje tři konstanty, které poskytují informace o konfiguraci na národní prostředí omezující vlastnosti deklarované v [ \<codecvt>](../standard-library/codecvt.md). Odlišné hodnoty jsou:

- `consume_header`, aby byla při čtení vícebajtové sekvence spotřebována počáteční sekvenci záhlaví a určila endianness následující vícebajtové sekvence, která má být přečtena

- `generate_header`, chcete-li generovat počáteční sekvenci záhlaví při zápisu vícebajtové sekvence k inzerování endianness následné vícebajtové sekvence, která má být zapsána

- `little_endian`, chcete-li generovat vícebajtovou sekvenci v pořadí little-endian, na rozdíl od výchozího pořadí big-endian

Tyto konstanty mohou být ORed společně v libovolné kombinace.

## <a name="see-also"></a>Viz také

[\<kodek>](../standard-library/codecvt.md)
