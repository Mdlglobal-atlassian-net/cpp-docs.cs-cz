---
title: "Chyba sestavení projektu PRJ0025 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0025
dev_langs:
- C++
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f99a57439e87e1841555c90326072ba1667b6b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0025"></a>Chyba sestavení projektu PRJ0025
Dávkový soubor 'file' obsahuje obsah kódování Unicode, které nebylo možné přeložit na uživatele ANSI znakovou stránku.  
  
 ***UNICODE obsah souboru***  
  
 Systém projektu najít obsah kódování Unicode v vlastní sestavení pravidla nebo vytvořit událost, která nemůže správně přeložit na uživatele aktuální ANSI znakovou stránku.  
  
 Řešením této chyby je aktualizovat obsah pravidla sestavení nebo události použít ANSI nebo na počítač nainstalujte znakovou stránku a nastavte jej jako výchozí systémové nastavení sestavení.  
  
 Další informace o vlastní kroky sestavení a události sestavení, najdete v části [Principy vlastní kroky sestavení a události sestavení](../../ide/understanding-custom-build-steps-and-build-events.md).