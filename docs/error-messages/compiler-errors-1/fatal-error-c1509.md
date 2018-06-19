---
title: Závažná chyba C1509 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fec83f6b6138eacc613e560b9da4557079d6677d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198791"
---
# <a name="fatal-error-c1509"></a>Závažná chyba C1509
omezení kompilátoru: příliš mnoho stavy obslužné rutiny výjimek ve funkci 'function'. zjednodušení – funkce  
  
 Kód překračuje vnitřní limit na stavy obslužné rutiny výjimek (32 768 stavy).  
  
 Nejčastější příčinou je, že funkce obsahuje složitý výraz uživatelsky definované třídy, proměnných a aritmetické operátory.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Výrazy Zjednodušte přiřazením běžné podvýrazy dočasné proměnné.  
  
2.  Funkce rozdělení na menší funkce.