---
title: "Závažná chyba C1004 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1004
dev_langs: C++
helpviewer_keywords: C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c6a9e74d7918e1cb2c9190c87f4f1ec75f89237b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1004"></a>Závažná chyba C1004
Neočekávaný konec souboru nalezen  
  
 Kompilátor bylo dosaženo konce zdrojového souboru bez vyřešení konstrukt. Kód mohou chybět jeden z následujících elementů:  
  
-   Pravé složené závorce  
  
-   Pravá závorka  
  
-   Uzavírající komentář značky (* nebo)  
  
-   Středníkem  
  
 Chcete-li tuto chybu vyřešit, zkontrolujte následující:  
  
-   Výchozí diskové jednotce není dostatek místa pro dočasné soubory, které vyžadují o dvakrát tolik místa jako zdrojový soubor.  
  
-   `#if` Direktiva, která vyhodnocena jako false nemá uzavírací `#endif` – direktiva.  
  
-   Zdrojový soubor nemá na konci znaky CR a odřádkování.  
  
 Následující ukázka generuje C1004:  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 Možná řešení:  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```