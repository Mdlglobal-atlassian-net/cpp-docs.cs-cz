---
title: Závažná chyba C1004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1004
dev_langs:
- C++
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88f76c00c8f5b36acf238f0da88e908eac6dbe8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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