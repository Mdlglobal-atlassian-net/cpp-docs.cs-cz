---
title: implementation_only – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- implementation_only
dev_langs:
- C++
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0496a1f76a763ae7c7a2e95c1b68fa08089e2c4f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374023"
---
# <a name="implementationonly"></a>implementation_only
**Specifické pro C++**  
  
Potlačí generování souboru .tlh hlavičky (primární hlavičkový soubor).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>Poznámky  
 
Tento soubor obsahuje všechny deklarace, na které se používá k vystavení obsah knihovny typů. Záhlaví souboru tli, s implementacemi členské funkce obálky se vygeneruje a zahrnout do kompilace.  
  
Pokud tento atribut je zadána, je obsah hlavičky tli v stejný obor názvů, jako je obvykle používají v hlavičce .tlh. Kromě toho členské funkce nejsou deklarovány jako vložené.  
  
**Implementation_only –** atribut je určena pro použití ve spojení s [no_implementation –](../preprocessor/no-implementation.md) atribut jako způsob, jak zachovat implementace mimo soubor předkompilované hlavičky (PCH). `#import` Příkaz `no_implementation` atribut je umístěn ve zdrojové oblasti použité k vytvoření soubor PCH. Výsledný soubor PCH se používá několik zdrojových souborů. `#import` Příkaz **implementation_only –** mimo oblast PCH se pak použije atribut. Je nutné použít tento příkaz pouze jednou v jednom ze zdrojových souborů. Tím se vygeneruje všechny požadované obálky členské funkce bez další rekompilace pro každý zdrojový soubor.  
  
> [!NOTE]
> **Implementation_only –** atribut v jednom `#import` příkaz musí být ve spojení s jiným `#import` prohlášení o stejný typ knihovny, s `no_implementation` atribut. V opačném případě se nevygeneruje chyby kompilátoru. Důvodem je, že generované obálkové třídy definice `#import` příkaz `no_implementation` atributů je potřeba kompilovat implementace generovaných **implementation_only –** atribut.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)