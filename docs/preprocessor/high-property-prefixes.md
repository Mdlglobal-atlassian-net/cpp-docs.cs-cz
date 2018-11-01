---
title: high_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 130d19f275612e153955ae49f299fe2f36d098bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579813"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes

**Specifické pro C++**

Určuje alternativní předpony pro tři metody vlastností.

## <a name="syntax"></a>Syntaxe

```
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Parametry

*GetPrefix*<br/>
Předpona se použije pro `propget` metody.

*PutPrefix*<br/>
Předpona se použije pro `propput` metody.

*PutRefPrefix*<br/>
Předpona se použije pro `propputref` metody.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení základní zpracování chyb `propget`, `propput`, a `propputref` metody jsou vystaveny členským funkcím pojmenovaným s předponami `Get`, `Put`, a `PutRef`v uvedeném pořadí.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)