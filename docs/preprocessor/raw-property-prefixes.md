---
title: raw_property_prefixes – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1170440428a5c92e383152826827989d602e69fb
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808735"
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