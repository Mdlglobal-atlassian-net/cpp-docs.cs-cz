---
title: "Specifikátory třídy úložiště s deklaracemi funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f7d8b6ba1c0287492195ee891b1a573bf74de6cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Specifikátory třídy úložiště s deklaracemi funkce
Můžete použít buď **statické** nebo `extern` specifikátor třídy úložiště v deklaracích funkce. Funkce mají vždy globální životnost.  
  
 **Konkrétní Microsoft**  
  
 Deklarace funkce na vnitřní úrovni mají stejný význam jako deklarace funkce na vnější úrovni. To znamená, že funkce je viditelná z místa deklarace ve zbytku jednotky překladu i v případě, že je deklarována v místním oboru.  
  
 **Konkrétní Microsoft END**  
  
 Pravidla viditelnosti pro funkce se mírně liší od pravidel pro proměnné, a to takto:  
  
-   Funkce deklarován jako **statické** je viditelná pouze v rámci zdrojový soubor, ve kterém je definovaný. Můžete volat funkce ve stejném souboru zdroje **statické** funkce, ale funguje v jiných zdrojových souborů nelze přistupovat přímo podle názvu. Je možné deklarovat jiné **statické** funkce se stejným názvem v různých zdrojového souboru bez konfliktů.  
  
-   Funkce deklarované jako `extern` jsou zobrazována prostřednictvím všechny zdrojové soubory v programu (Pokud později redeclare funkce, jako **statické**). Jakákoli funkce může volat funkci deklarovanou jako `extern`.  
  
-   Deklarace funkce, které vynechávají specifikátor třídy úložiště, jsou ve výchozím nastavení deklarovány jako `extern`.  
  
 **Konkrétní Microsoft**  
  
 Microsoft umožňuje předefinování `extern` identifikátor jako **statické**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Třídy úložiště jazyka C](../c-language/c-storage-classes.md)