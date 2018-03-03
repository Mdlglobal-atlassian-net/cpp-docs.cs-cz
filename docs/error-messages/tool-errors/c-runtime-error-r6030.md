---
title: "Za r6030 jazyka C Chyba v běhu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bc7c5db2b486ef051975c0e8d31d6c24ca5aa6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6030"></a>Za r6030 jazyka C Chyba za běhu
CRT nebyla inicializována  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má internímu problému. Tento problém je nejčastěji způsobeno určité softwarové programy zabezpečení, nebo jen zřídka, chyby v programu.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Konkrétní pokyny pro minimalizaci tento problém může mít zabezpečovací software. Zkontrolujte webu dodavatele softwaru zabezpečení podrobnosti. Alternativně kontrolovat aktualizované verze softwaru zabezpečení nebo zkuste jinou zabezpečení softwaru.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 K této chybě dojde, pokud používáte C Runtime (CRT), ale neprovedl kód CRT spuštění. Je možné k této chybě, pokud přepínač linkeru [/Entry](../../build/reference/entry-entry-point-symbol.md) k přepsání výchozí počáteční adresa, obvykle se používá **mainCRTStartup**, **wmainCRTStartup** pro konzole EXE **WinMainCRTStartup** nebo **wWinMainCRTStartup** pro Windows EXE, nebo **_DllMainCRTStartup** pro knihovnu DLL. Pokud jeden z výše uvedené funkce je volána při spuštění, nebudou inicializována C Runtime. Tyto funkce spuštění se nazývají normálně ve výchozím nastavení, když propojit běhové knihovny jazyka C a normální **hlavní**, **wmain**, **WinMain**, nebo  **DllMain** vstupní body.  
  
 Je také možné se tato chyba zobrazí, pokud jiný program používá techniky vkládání kódu pro určité volání knihovny DLL pro depeše. Některé programy nežádoucí zabezpečení použijte tento postup. Ve verzích Visual C++ před Visual Studio 2015 je možné použít staticky propojené knihovny CRT k vyřešení příslušného problému, ale to není doporučeno důvodů aktualizace zabezpečení a aplikace. Odstranění tohoto problému může vyžadovat akce koncového uživatele.