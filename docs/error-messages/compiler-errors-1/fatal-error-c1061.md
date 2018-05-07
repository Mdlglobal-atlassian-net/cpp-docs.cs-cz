---
title: Závažná chyba C1061 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1061
dev_langs:
- C++
helpviewer_keywords:
- C1061
ms.assetid: 9366c0bc-96e0-4967-aa7d-4ebf098de806
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fde2d3a076b4cf78a8104fd19719bec205828c68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1061"></a>Závažná chyba C1061
Omezení kompilátoru: bloky jsou vnořeny příliš hluboko  
  
 Vnoření bloků kódu překračuje limit 128 úrovní vnoření. Jedná se o pevný limit kompilátoru pro jazyky C a C++ v 32bitové i 64bitové sadě nástrojů. Počet úrovní vnoření lze zvýšit pomocí čehokoli, co vytvoří obor nebo blok. Úroveň vnoření, kterou pozoruje kompilátor, dokážou zvýšit například obory názvů, direktivy using, rozšíření preprocesoru, rozšíření šablon, zpracování výjimek, konstrukce smyček a klauzule else-if.  
  
 Chcete-li tuto chybu vyřešit, musíte kód refaktorovat. Hluboce vnořený kód je v každém případě obtížně pochopitelný a odůvodnitelný. Refaktoring kódu tak, aby měl menší počet úrovní vnoření, může vylepšit kvalitu kódu a zjednodušit údržbu. Hluboce vnořený kód rozdělte na funkce, které jsou volány z původního kontextu. Omezte počet smyček nebo zřetězených klauzulí else-if uvnitř bloku.