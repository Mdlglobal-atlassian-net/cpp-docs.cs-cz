---
title: high_property_prefixes – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3932a7632b12120e722c5f375f4387e08f1853b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809054"
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