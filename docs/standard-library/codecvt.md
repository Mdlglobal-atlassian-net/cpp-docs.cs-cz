---
title: '&lt;codecvt –&gt;'
ms.date: 11/04/2016
f1_keywords:
- codecvt
- <codecvt>
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
ms.openlocfilehash: 56cd4263d3dcddd23246a05466275b8b7d370b95
ms.sourcegitcommit: fe1e21df175cd004d21c6e4659082efceb649a8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978241"
---
# <a name="ltcodecvtgt"></a>&lt;codecvt –&gt;

Definuje několik tříd šablon, které popisují objekty na základě šablony třídy [codecvt](../standard-library/codecvt-class.md). Tyto objekty může sloužit jako [omezující vlastnosti národního prostředí](../standard-library/locale-class.md#facet_class) , které řídí převodů mezi sekvencí hodnot typu `Elem` a sekvencí hodnot typu **char**.

## <a name="syntax"></a>Syntaxe

```cpp
#include <codecvt>
```

## <a name="remarks"></a>Poznámky

Omezující vlastnosti národního prostředí, které jsou deklarované v této hlavičky převod mezi několika kódování znaků. Pro široké znaky (uložené v rámci programu v celých čísel pevné velikosti):

- UCS-4 je v rámci programu jako 32bitové celé číslo kódování Unicode (ISO 10646).

- UCS-2 je v programu jako 16bitové celé číslo v kódování Unicode.

- UTF-16 je Unicode kódované v rámci programu jako jeden nebo dva 16bitová celá čísla. (Všimněte si, že nesplňuje všechny požadavky platné kódování širokých znaků pro Standard C nebo Standard C++. Nicméně se běžně používá jako takové.)

Pro datové proudy bajtů (uložené v souboru, jako sekvence bajtů nepřenáší ani neukládá v rámci programu v poli **char**):

- UTF-8 je zakódován jako jednoho nebo více bajtů osmibitové s pořadím bajtů deterministické v rámci datového proudu bajtů kódování Unicode.

- Je v rámci datového proudu bajtů jako UTF-16 kódování Unicode UTF-16LE s 16bitové celé číslo nejprve zobrazí jako dva bajty osmibitové méně významný bajt.

- Je v rámci datového proudu bajtů jako UTF-16 kódování Unicode UTF-16BE s 16bitové celé číslo nejprve zobrazí jako dva bajty osmibitové, více významný bajt.

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Určuje konfigurační informace pro omezující vlastnosti národního prostředí.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|Představuje omezující vlastnost národního prostředí, který převede mezi široké znaky zakódován jako UCS-2 nebo UCS-4 a datový proud bajtů kódováním UTF-8.|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Představuje omezující vlastnost národního prostředí, který převede mezi široké znaky s kódováním UTF-16 a datový proud bajtů kódováním UTF-8.|
|[codecvt_utf16](codecvt-utf16-class.md)|Představuje omezující vlastnost národního prostředí, který převede mezi široké znaky zakódován jako UCS-2 nebo UCS-4 a kódováním UTF-16LE nebo UTF-16BE datový proud bajtů.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<codecvt – >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
