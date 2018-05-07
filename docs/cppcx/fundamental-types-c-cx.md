---
title: Základní typy (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0da64edaa3f94ac9813408d936e3f83783e6b241
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fundamental-types-ccx"></a>Základní typy (C + +/ CX)
Kromě standardní C++ předdefinovaných typů C + +/ CX podporuje systém typů, který je definován pomocí prostředí Windows Runtime architektura tím, že poskytuje – definice TypeDef pro prostředí Windows Runtime základní typy, které jsou namapovány na standardní typy C++... C + +/ CX implementuje logická hodnota, znaku a číselné základní typy. Tyto definice TypeDef jsou definovány v `default` obor názvů, který se nikdy musí být explicitně určen. Kromě toho, C + +/ CX poskytuje konkrétní implementace a obálek pro určité typy prostředí Windows Runtime a rozhraní.  
  
## <a name="boolean-and-character-types"></a>Logická hodnota a znak typy  
 Následující tabulka uvádí předdefinované logické a typů znaků a jejich ekvivalenty u standardní C++.  
  
|Obor názvů|C + +/ CX název|Definice|Standardní C++ název|Hodnoty rozsahu|  
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|Platforma|Boolean|8bitové logická hodnota.|bool|`true` (nenulové) a `false` (nula).|  
|default|char16|16bitové nečíselnou hodnotu, která představuje bod kódování Unicode (UTF-16).|wchar_t<br /><br /> -nebo-<br /><br /> L'c.|(Zadaný pomocí standardu Unicode)|  
  
## <a name="numeric-types"></a>Číselné typy  
 Následující tabulka uvádí předdefinované číselnými typy. Číselné typy jsou deklarované v `default` obor názvů a se definice TypeDef pro odpovídající typ předdefinované C++. V prostředí Windows Runtime jsou podporovány všechny C++ předdefinovaných typů (například pokud). Konzistence a srozumitelnější, doporučujeme vám použít C + +/ CX název.  
  
|C + +/ CX název|Definice|Standardní C++ název|Hodnoty rozsahu|  
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|  
|int8|8bitové podepsaný číselnou hodnotu.|podepsaný char|-128 až 127|  
|uint8|8bitové nepodepsané číselnou hodnotu.|unsigned char|0 až 255|  
|Int16|16bitové znaménkem.|short|-32 768 do 32 767|  
|UInt16|16bitové celé číslo bez znaménka.|unsigned short|0 až 65 535|  
|int32|32-bit znaménkem.|int|-2,147,483,648 prostřednictvím 2 147 483 647|  
|UInt32|32bitové celé číslo bez znaménka.|unsigned int|0 až 4 294 967 295|  
|int64|64bitová verze znaménkem.|dlouhé dlouho - nebo - __int64|-9,223,372,036,854, 775,808 prostřednictvím 9,223,372,036,854,775,807|  
|UInt64|64bitové celé číslo bez znaménka.|nepodepsané __int64 dlouho dlouho - nebo - bez znaménka|0 až 18,446,744,073,709,551,615|  
|Float32|IEEE 754 32-bit s plovoucí desetinnou čárkou číslo.|float|3.4e +/-38 (7 míst)|  
|Float64|IEEE 754 64-bit s plovoucí desetinnou čárkou číslo.|double|1, 7E +/-308 (15 číslic)|  
  
## <a name="windows-runtime-types"></a>Typy systému Windows Runtime  
 Následující tabulka uvádí některé další typy, které jsou definovány architektury prostředí Windows Runtime a jsou integrovány v jazyce C + +/ CX. Objekt a řetězec jsou odkazové typy. Ostatní jsou typy hodnot. Všechny tyto typy jsou deklarované v `Platform` oboru názvů. Úplný seznam najdete v tématu [obor názvů Platform](../cppcx/platform-namespace-c-cx.md).  
  
|Název|Definice|  
|----------|----------------|  
|Objekt|Představuje jakýkoli typ prostředí Windows Runtime.|  
|String|Posloupnost znaků, které představují text.|  
|Rect –|Sada čtyři desetinná čísla, které představují umístění a velikost obdélníku.|  
|SizeT|Seřazené dvojici čísel s plovoucí desetinnou čárkou, zadáte výškou a šířkou.|  
|bod|Seřazené dvojici s plovoucí desetinnou čárkou souřadnice x a y souřadnice, které definují bod do dvourozměrné roviny.|  
|Identifikátor GUID|Hodnoty jiné než číselné 128-bit, která slouží jako jedinečný identifikátor.|  
|UIntPtr|(Pouze pro interní použití.) Nepodepsané hodnotu 64-bit, která slouží jako ukazatel.|  
|IntPtr|(Pouze pro interní použití.)  Podepsaný 64 bitů hodnotu, která slouží jako ukazatel.|  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)