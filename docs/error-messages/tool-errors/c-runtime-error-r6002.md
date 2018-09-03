---
title: C R6002 Chyba v běhu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50a970ecea4fdd7d397c09672b0548be947cab1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298561"
---
# <a name="c-runtime-error-r6002"></a>R6002 Chyba za běhu C
podpora plovoucí desetinné čárky není načtená.  
  
 Nebyl propojeny potřebné knihovny s plovoucí desetinnou čárkou.  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má internímu problému. Existuje několik možných příčin této chyby, avšak často je způsobeno značit potíže v kódu aplikace, nebo při spuštění aplikace, který nebyl vytvořen pro konkrétní počítač procesor.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 Této chybě může dojít v aplikaci při nebyl propojení s plovoucí desetinnou čárkou knihovny. Kontrola pro jednu z těchto příčin:  
  
-   Řetězec formátu pro `printf_s` nebo `scanf_s` funkce obsahuje specifikaci formátu s plovoucí desetinnou čárkou a program neobsahuje žádné hodnoty s plovoucí desetinnou čárkou nebo proměnné. Chcete-li tento problém vyřešit, použijte s plovoucí desetinnou čárkou argument tak, aby odpovídaly specifikace formátu s plovoucí desetinnou čárkou nebo proveďte s plovoucí desetinnou čárkou přiřazení jinde v programu. To způsobí, že podpora plovoucí desetinné čárky má být načten.  
  
-   Kompilátor minimalizuje velikost programu načtením podpora plovoucí desetinné čárky pouze v případě potřeby. Kompilátor nerozpozná operace s plovoucí desetinnou čárkou nebo specifikace formátu s plovoucí desetinnou čárkou ve formátu řetězce, takže nenačte rutiny nezbytné s plovoucí desetinnou čárkou. Chcete-li tento problém vyřešit, použijte specifikace formátu s plovoucí desetinnou čárkou a zadejte argument s plovoucí desetinnou čárkou nebo proveďte s plovoucí desetinnou čárkou přiřazení jinde v programu. To způsobí, že podpora plovoucí desetinné čárky má být načten.  
  
-   V programu smíšený jazyk knihovnu C zadanou před knihovnu FORTRAN při program byl propojení. Znovu připojit a zadejte knihovnu, která C poslední.