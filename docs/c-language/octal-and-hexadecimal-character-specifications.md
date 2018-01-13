---
title: "Specifikace osmičkových a šestnáctkových znaků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf3a27dc61543482d1d6484d0edd4b5e1bb04373
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Specifikace osmičkových a šestnáctkových znaků
Pořadí  **\\**  *ooo* znamená můžete zadat libovolný znak v ASCII znaková sada jako osmičková znak třímístné kód. Číselná hodnota osmičkového čísla určuje hodnotu požadovaného znaku nebo širokého znaku.  
  
 Podobně pořadí **\x***hhh* můžete zadat libovolný znak ASCII jako kód hexadecimálních znaků. Například můžete udělit backspace znaků ASCII jako normální řídicí sekvence jazyka C (**\b**), nebo můžete jej jako code **\010** (osmičková) nebo **\x008** (hexadecimální).  
  
 V osmičkové řídicí sekvenci lze použít pouze číslice 0 až 7. Osmičkové řídicí sekvence nemohou být nikdy delší než tři číslice a jsou ukončeny prvním znakem, který není osmičkovou číslicí. Přestože není nutné použít všechny tři číslice, je třeba použít nejméně jednu. Je třeba osmičková reprezentace **\10** pro backspace znaků ASCII a **\101** pro písmeno A jak je uveden v ASCII grafu.  
  
 Podobně je třeba použít alespoň jednu číslici šestnáctkové řídicí sekvence, ale lze vynechat druhou a třetí číslici. Proto můžete zadat šestnáctková řídicí sekvence backspace znaku, protože buď **\x8**, **\x08**, nebo **\x008**.  
  
 Hodnota osmičková nebo šestnáctková řídicí sekvence musí být v rozsahu reprezentovat hodnot pro typ **nepodepsané char** pro konstanta znaků a typ `wchar_t` pro široká charakterová konstanta. V tématu [vícebajtové a široké znaky](../c-language/multibyte-and-wide-characters.md) informace o široká charakterová konstanty.  
  
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