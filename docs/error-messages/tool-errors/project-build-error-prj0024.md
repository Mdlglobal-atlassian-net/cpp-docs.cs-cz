---
title: Chyba sestavení projektu PRJ0024 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59bf76aba80093bf9e8e653bdfb9fad49687a501
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318344"
---
# <a name="project-build-error-prj0024"></a>Chyba sestavení projektu PRJ0024
Cesta Unicode 'path' nebylo možné přeložit na uživatele ANSI znakovou stránku.  
  
 ***cesta*** je původní verze Unicode řetězec cesty. Této chybě může dojít v případech, kde je cesta znakové sady Unicode, který nelze převést přímo na ANSI pro aktuální stránku kódu systému.  
  
 Této chybě může dojít, pokud pracujete s projektem, která byla vyvinuta v systému pomocí znakové stránky, který není ve vašem počítači.  
  
 Řešením této chyby je aktualizujte cestu k použijte ANSI text nebo k na počítač nainstalujte znakovou stránku a nastavte jej jako výchozí systémové nastavení.