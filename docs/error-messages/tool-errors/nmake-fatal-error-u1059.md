---
title: Závažná chyba nástroje NMAKE U1059 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb038befdb7c587c6fe2a734003abba585c3e2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1059"></a>Závažná chyba nástroje NMAKE U1059
Chyba syntaxe: '}' v závislé chybí  
  
 Cesta hledání pro závislé byl nesprávně zadán. Buď místo existovalo v cesta nebo složená závorka (**}**) byl vynechán.  
  
 Syntaxe pro specifikaci adresáře pro závislé je  
  
 **{**   
 ***adresáře* } závislé**  
  
 kde `directories` Určuje jeden nebo více cest, každé oddělené středníkem (**;**). Žádné mezery.  
  
 Pokud část hodnoty nebo celou cestu k vyhledávání je nahrazena makra, ujistěte se, že neexistují žádné mezery v rozšíření – makro.