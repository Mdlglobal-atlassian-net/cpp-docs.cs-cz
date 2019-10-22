---
title: '&lt;codecvt &gt;'
ms.date: 11/04/2016
f1_keywords:
- codecvt
- <codecvt>
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
ms.openlocfilehash: 972672e80ce4f82402296317c75e35dcd10c9e93
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688287"
---
# <a name="ltcodecvtgt"></a>&lt;codecvt &gt;

Definuje několik šablon třídy, které popisují objekty založené na šabloně třídy [codecvt](../standard-library/codecvt-class.md). Tyto objekty mohou sloužit jako [omezující vlastnosti národního prostředí](../standard-library/locale-class.md#facet_class) , které řídí převody mezi sekvencí hodnot typu `Elem` a sekvencí hodnot typu **char**.

## <a name="syntax"></a>Syntaxe

```cpp
#include <codecvt>
```

## <a name="remarks"></a>Poznámky

Omezující vlastnosti národního prostředí deklarované v této hlavičce převádějí mezi několika kódováními znaků. Pro velké znaky (uložené v programu v celých číslech s pevnou velikostí):

- UCS-4 je Unicode (ISO 10646) kódovaný v programu jako 32 celé číslo.

- UCS-2 je kódování Unicode kódované v programu jako 16bitové celé číslo.

- UTF-16 je kódování Unicode kódované v rámci programu jako jedno nebo 2 16 celé číslo. (Všimněte si, že se neshodují se všemi požadavky na platné kódování ve velkých znacích Standard C nebo standard C++. Nicméně se běžně používá jako takový.)

Pro bajtové datové proudy (uložené v souboru, přenesené jako bajtové sekvenci nebo uložené v rámci programu v poli **char**):

- UTF-8 je kódování Unicode kódované v rámci bajtového datového proudu jako jedna nebo více osmi bitových bajtů s deterministickým pořadím bajtů.

- UTF-16LE je kódování Unicode kódované v rámci bajtového datového proudu jako UTF-16 s každým 16 bitovým číslem uvedeným jako 2 8 bajtů, což je méně významný bajt jako první.

- UTF-16BE je kódování Unicode kódované v rámci bajtového datového proudu jako UTF-16 s každým 16 bitovým číslem uvedeným jako 2 8 bajtů, a to mnohem významnějšího bajtu.

### <a name="enumerations"></a>Výčty

|||
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Určuje informace o konfiguraci pro omezující vlastnosti národního prostředí.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|Představuje omezující vlastnost národního prostředí, která převádí mezi znaky zakódovanými jako UCS-2 nebo UCS-4 a datový proud bajtů kódovaný jako UTF-8.|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Představuje omezující vlastnost národního prostředí, která je převedena mezi velké znaky kódované jako UTF-16 a datový proud bajtů kódovaný jako UTF-8.|
|[codecvt_utf16](codecvt-utf16-class.md)|Představuje omezující vlastnost národního prostředí, která je převedena mezi velké znaky kódované jako UCS-2 nebo UCS-4 a datový proud bajtů kódovaný jako UTF-16LE nebo UTF-16BE.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<codecvt >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
