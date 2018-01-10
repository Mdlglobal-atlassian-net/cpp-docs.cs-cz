---
title: "Závažná chyba C1055 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1055
dev_langs: C++
helpviewer_keywords: C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bfdd971dfcb5c762346a8d1f59452f31826db296
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1055"></a>Závažná chyba C1055
omezení kompilátoru: mimo klíče  
  
 Zdrojový soubor obsahuje příliš mnoho symboly. Kompilátor nemá dostatek klíče hash pro tabulky symbolů.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zdrojový soubor rozdělte do menších souborů.  
  
2.  Vyloučení nepotřebných hlavičkových souborů.  
  
3.  Znovu použít dočasné a globální proměnné místo vytvoření nové.