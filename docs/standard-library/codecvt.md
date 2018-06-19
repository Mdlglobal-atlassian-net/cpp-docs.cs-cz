---
title: '&lt;codecvt –&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt
- <codecvt>
dev_langs:
- C++
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d4e07c4869bd345e77f0af4f30f694773aed114
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845138"
---
# <a name="ltcodecvtgt"></a>&lt;Codecvt –&gt;

Definuje několik tříd šablon, které popisují objekty na základě šablony třídy [codecvt –](../standard-library/codecvt-class.md). Tyto objekty může sloužit jako [omezující vlastnosti národního prostředí](../standard-library/locale-class.md#facet_class) , řídit převody mezi pořadí hodnot typu `Elem` a pořadí hodnot typu `char`.

## <a name="syntax"></a>Syntaxe

```cpp
#include <codecvt>

```

## <a name="remarks"></a>Poznámky

Národní prostředí omezující vlastnosti deklarované v tuto hlavičku převod mezi několik kódování znaků. Široké znaky (uložené v rámci programu v pevné velikosti celá čísla):

- UCS 4 je v rámci programu jako 32bitové celé číslo kódování Unicode (ISO 10646).

- UCS-2 je v rámci programu jako 16bitové celé číslo kódování Unicode.

- Znakové sady UTF-16 je Unicode kódovaný v rámci programu jako jedna nebo dvě celá čísla 16 bitů. (Všimněte si, že nesplňuje všechny požadavky platný široká charakterová kódování pro standardní C nebo C++ standardní. Nicméně se často používá jako takový.)

Pro bajtové datové proudy (uložené v souboru, přenášených jako pořadí bajtů nebo uložené v rámci programu v pole `char`):

- Znakové sady UTF-8 je kódovaná jako jeden nebo více osm bitových hodnot s pořadím bajtů deterministickou v rámci datového proudu bajtů kódování Unicode.

- Znakové sady UTF-16LE je v datovém proudu bajtů jako UTF-16 kódování Unicode s 16bitové celé číslo uvedené jako dva bajty osm bitů, méně významný bajt nejdřív.

- Znakové sady UTF-16BE je v datovém proudu bajtů jako UTF-16 kódování Unicode s 16bitové celé číslo uvedené jako dva bajty osm bitů, více významný bajt nejdřív.

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Určuje konfigurační informace pro omezující vlastnosti národního prostředí.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|Představuje národní prostředí omezující vlastnosti, který převádí mezi široké znaky kódovaná jako UCS-2 nebo UCS 4 a datového proudu bajtů kódovaná jako UTF-8.|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Představuje národní prostředí omezující vlastnosti, který převádí mezi široké kódováním UTF-16 znaků a datového proudu bajtů kódovaná jako UTF-8.|
|[codecvt_utf16](codecvt-utf16-class.md)|Představuje národní prostředí omezující vlastnosti, který převádí mezi široké znaky kódovaná jako UCS-2 nebo UCS 4 a datového proudu bajtů kódování UTF-16LE nebo UTF-16BE.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<codecvt – >

**Namespace:** stdt

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
