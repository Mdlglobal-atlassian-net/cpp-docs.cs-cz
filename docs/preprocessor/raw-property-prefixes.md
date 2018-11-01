---
title: raw_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 1e44b5265e486f0e5b5896bed41b62ebbdaa4fd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647133"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes

**Specifické pro C++**

Určuje alternativní předpony pro tři metody vlastností.

## <a name="syntax"></a>Syntaxe

```
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Parametry

*GetPrefix*<br/>
Předpona se použije pro `propget` metody.

*PutPrefix*<br/>
Předpona se použije pro `propput` metody.

*PutRefPrefix*<br/>
Předpona se použije pro `propputref` metody.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení, nízké úrovně `propget`, `propput`, a `propputref` metody jsou vystaveny členským funkcím pojmenovaným s **get_**, **put_**, a **putref_** v uvedeném pořadí. Tyto předpony jsou kompatibilní s názvy používanými v souborech hlaviček generovaných jazykem MIDL.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)