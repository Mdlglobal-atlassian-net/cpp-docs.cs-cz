---
title: Specifikace osmičkových a šestnáctkových znaků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eeb1f8e08fbb1d4f30517485c9296febab5a0de0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198753"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Specifikace osmičkových a šestnáctkových znaků
Sekvence **\\** <em>ooo</em> znamená, že můžete zadat libovolný znak ASCII znaková sada jako trojmístný osmičkový kód znaku. Číselná hodnota osmičkového čísla určuje hodnotu požadovaného znaku nebo širokého znaku.  
  
 Podobně sekvence **\x**<em>hhh</em> můžete zadat libovolný znak ASCII jako šestnáctkový kód znaku. Například můžete poskytnout backspace znak ASCII jako normální řídicí sekvenci jazyka C (**\b**), nebo kód jako **\010** (Osmičkově) nebo **\x008** (šestnáctkově).  
  
 V osmičkové řídicí sekvenci lze použít pouze číslice 0 až 7. Osmičkové řídicí sekvence nemohou být nikdy delší než tři číslice a jsou ukončeny prvním znakem, který není osmičkovou číslicí. Přestože není nutné použít všechny tři číslice, je třeba použít nejméně jednu. Například osmičkové vyjádření je **\10** pro znak ASCII backspace a **\101** písmene, jak je uvedeno v ASCII grafu.  
  
 Podobně je třeba použít alespoň jednu číslici šestnáctkové řídicí sekvence, ale lze vynechat druhou a třetí číslici. Lze tedy zadat šestnáctkovou řídicí sekvenci znaku backspace jako buď **\x8**, **\x08**, nebo **\x008**.  
  
 Hodnoty šestnáctkové nebo osmičkové řídicí sekvence musí být v rozsahu hodnot reprezentovatelných typem **unsigned char** pro znakovou konstantu a typem `wchar_t` pro konstantu širokého znaku. Zobrazit [vícebajtové a široké znaky](../c-language/multibyte-and-wide-characters.md) o konstanty širokého znaku.  
  
 Na rozdíl od osmičkové řídicí konstanty není počet šestnáctkových číslic v řídicí sekvenci nijak omezen. Šestnáctková řídicí sekvence se ukončí na prvním znaku, který není šestnáctkovou číslicí. Protože šestnáctkové číslice používají písmena a **až f**, je nutné se ujistit, že řídicí sekvence končí zamýšlenou číslicí. Aby nedocházelo k záměně, lze znak šestnáctkové nebo osmičkové definice umístit do definice makra:  
  
```  
#define Bell '\x07'  
```  
  
 U šestnáctkových hodnot je možné řetězec přerušit pro zřetelné zobrazení správné hodnoty:  
  
```  
"\xabc"    /* one character  */  
"\xab" "c" /* two characters */  
```  
  
## <a name="see-also"></a>Viz také  
 [Konstanty znaků jazyka C](../c-language/c-character-constants.md)