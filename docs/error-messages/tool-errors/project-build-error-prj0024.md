---
title: "Chyba sestavení projektu PRJ0024 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0024
dev_langs: C++
helpviewer_keywords: PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cfd51c58fa11ae19c014365dbfbc57c6cd7eb687
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0024"></a>Chyba sestavení projektu PRJ0024
Cesta Unicode 'path' nebylo možné přeložit na uživatele ANSI znakovou stránku.  
  
 ***cesta*** je původní verze Unicode řetězec cesty. Této chybě může dojít v případech, kde je cesta znakové sady Unicode, který nelze převést přímo na ANSI pro aktuální stránku kódu systému.  
  
 Této chybě může dojít, pokud pracujete s projektem, která byla vyvinuta v systému pomocí znakové stránky, který není ve vašem počítači.  
  
 Řešením této chyby je aktualizujte cestu k použijte ANSI text nebo k na počítač nainstalujte znakovou stránku a nastavte jej jako výchozí systémové nastavení.