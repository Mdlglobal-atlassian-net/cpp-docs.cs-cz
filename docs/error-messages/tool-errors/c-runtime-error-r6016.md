---
title: "Chyba v běhu R6016 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6016
dev_langs:
- C++
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 451ff01b201b110ac5f05140e3b8581f1a8c2e28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6016"></a>R6016 Chyba za běhu C
Nedostatek místa pro data vlákna  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má problém s interní paměť. Existuje mnoho možných příčin této chyby, ale často je způsobeno podmínku velmi málo paměti chyb v aplikaci nebo chyby v add-in nebo rozšíření používané aplikace.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Ukončete ostatní spuštěné aplikace nebo restartujte počítač k uvolnění paměti.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat aplikaci.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** odebrat, opravit nebo znovu nainstalovat doplňky nebo rozšíření používané aplikace.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 K této chybě dojde, protože program nedostal z operačního systému pro dokončení dostatek paměti [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) nebo `_beginthreadex` volání nebo přístup z více vláken místní úložiště nebyla inicializována pomocí `_beginthread` nebo `_beginthreadex`.  
  
 Při spuštění nového vlákna musí knihovna vytvořit pro toto vlákno interní databázi. Pokud databázi nelze rozšířit pomocí paměti poskytované operačním systémem, vlákno se nespustí a volající proces se zastaví. K tomu může dojít, pokud proces vytvořil příliš mnoho vláken, nebo při vyčerpání místního úložiště vláken.  
  
 Doporučujeme spustitelné soubory, které volá běhové knihovny jazyka C (CRT) by měl použít `_beginthreadex` pro vytvoření přístup z více vláken, nikoli rozhraní API systému Windows `CreateThread`. `_beginthreadex`Inicializuje interní úložiště se statickými používá mnoho funkcí CRT v lokální úložiště vláken. Pokud používáte `CreateThread` vytvořit vlákno, CRT může ukončit proces s R6016 při volání funkce CRT, která vyžaduje inicializovaného interní úložiště se statickými.