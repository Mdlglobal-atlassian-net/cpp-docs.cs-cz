---
title: Specifikátory třídy úložiště s deklaracemi funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f84455dd29023194e64fa4e594419630ef2656e6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389660"
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