---
title: "Chyba sestavení projektu PRJ0033 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0cd7bcc0239ce88a19ae6009195f120a88be59ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0033"></a>Chyba sestavení projektu PRJ0033
Vlastnost 'Další závislosti, pro vlastní sestavovací krok pro 'file' obsažené 'Makro souboru, který vyhodnocuje se na 'macro_expansion'.  
  
 Vlastní krok sestavení na soubor obsahovala chybu v jeho dalších závislost pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamená, že je cesta chybně vytvořen, a to obsahující znaky, nebo kombinace znaků, které jsou neplatné v cestě k souboru.  
  
 Pokud chcete tuto chybu vyřešit, opravte makro nebo odstraňte specifikace cesty. Vyhodnotí cesta je absolutní cestu z adresáře projektu.