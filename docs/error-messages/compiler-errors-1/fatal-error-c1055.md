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
ms.openlocfilehash: 68b9dc5ac8a574111a678086a03e2760941e766f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1055"></a>Závažná chyba C1055
omezení kompilátoru: mimo klíče  
  
 Zdrojový soubor obsahuje příliš mnoho symboly. Kompilátor nemá dostatek klíče hash pro tabulky symbolů.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zdrojový soubor rozdělte do menších souborů.  
  
2.  Vyloučení nepotřebných hlavičkových souborů.  
  
3.  Znovu použít dočasné a globální proměnné místo vytvoření nové.