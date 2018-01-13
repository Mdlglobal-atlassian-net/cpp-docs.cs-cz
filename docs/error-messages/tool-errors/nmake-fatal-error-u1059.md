---
title: "Závažná chyba nástroje NMAKE U1059 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1059
dev_langs: C++
helpviewer_keywords: U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fb9ba98b0f82c158e4e11859e85af72efdbbc244
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1059"></a>Závažná chyba nástroje NMAKE U1059
Chyba syntaxe: '}' v závislé chybí  
  
 Cesta hledání pro závislé byl nesprávně zadán. Buď místo existovalo v cesta nebo složená závorka (**}**) byl vynechán.  
  
 Syntaxe pro specifikaci adresáře pro závislé je  
  
 **{**   
 ***adresáře* } závislé**  
  
 kde `directories` Určuje jeden nebo více cest, každé oddělené středníkem (**;**). Žádné mezery.  
  
 Pokud část hodnoty nebo celou cestu k vyhledávání je nahrazena makra, ujistěte se, že neexistují žádné mezery v rozšíření – makro.