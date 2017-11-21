---
title: "Chyba v běhu R6019 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6019
dev_langs: C++
helpviewer_keywords: R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 32b2b2f29b1b426ab67f089ae7a54a9730f16535
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
 K této chybě dojde, protože aplikace je volána funkce konzoly, ale operační systém neudělí přístup ke konzole. S výjimkou v režimu ladění, konzole funkce nejsou obvykle povoleny v aplikacích pro Windows Store. Pokud vaše aplikace vyžaduje oprávnění správce ke spuštění, ujistěte se, že je ve výchozím nastavení nainstalovaná spustit jako správce.