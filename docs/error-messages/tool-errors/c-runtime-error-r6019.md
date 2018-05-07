---
title: Chyba v běhu R6019 C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95950254d4a0611d9690b8636eb50f2fc1f0f264
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6019"></a>R6019 Chyba za běhu C
Nelze otevřít konzolu zařízení  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože jeho pokusu o přístup ke konzole, ale neměly dostatečná oprávnění. Existuje několik možných příčin této chyby, avšak je obvykle, protože program musí běžet jako správce, nebo v aplikaci je chyba.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Spuštění programu jako správce.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 K této chybě dojde, protože aplikace je volána funkce konzoly, ale operační systém neudělí přístup ke konzole. S výjimkou v režimu ladění, konzole funkce nejsou obvykle povoleny v aplikacích pro Store společnosti Microsoft. Pokud vaše aplikace vyžaduje oprávnění správce ke spuštění, ujistěte se, že je ve výchozím nastavení nainstalovaná spustit jako správce.