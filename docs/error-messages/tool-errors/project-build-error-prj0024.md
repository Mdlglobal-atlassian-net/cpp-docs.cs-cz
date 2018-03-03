---
title: "Chyba sestavení projektu PRJ0024 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cf9ad974856f132599932a32b954e50453adf56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0024"></a>Chyba sestavení projektu PRJ0024
Cesta Unicode 'path' nebylo možné přeložit na uživatele ANSI znakovou stránku.  
  
 ***cesta*** je původní verze Unicode řetězec cesty. Této chybě může dojít v případech, kde je cesta znakové sady Unicode, který nelze převést přímo na ANSI pro aktuální stránku kódu systému.  
  
 Této chybě může dojít, pokud pracujete s projektem, která byla vyvinuta v systému pomocí znakové stránky, který není ve vašem počítači.  
  
 Řešením této chyby je aktualizujte cestu k použijte ANSI text nebo k na počítač nainstalujte znakovou stránku a nastavte jej jako výchozí systémové nastavení.