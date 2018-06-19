---
title: Závažná chyba C1055 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07f0dc0e8dca08e8b0de47b73516d3fdfa21435b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225339"
---
# <a name="fatal-error-c1055"></a>Závažná chyba C1055
omezení kompilátoru: mimo klíče  
  
 Zdrojový soubor obsahuje příliš mnoho symboly. Kompilátor nemá dostatek klíče hash pro tabulky symbolů.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zdrojový soubor rozdělte do menších souborů.  
  
2.  Vyloučení nepotřebných hlavičkových souborů.  
  
3.  Znovu použít dočasné a globální proměnné místo vytvoření nové.