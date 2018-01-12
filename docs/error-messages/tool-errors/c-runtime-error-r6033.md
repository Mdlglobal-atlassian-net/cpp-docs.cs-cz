---
title: "Chyba za běhu C R6033 jazyka | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6033
dev_langs: C++
helpviewer_keywords: R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f2ef73d3cb82a65c8114d2e7f921b47ffd45d65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6033"></a>R6033 jazyka Chyba za běhu C
Pokus o použití MSIL kód z tohoto sestavení během inicializace nativního kódu. To znamená chyb v aplikaci. S největší pravděpodobností je výsledkem volání metody MSIL zkompilovaný (/ clr) funkce z konstruktoru nativní nebo zpracování funkce DllMain.  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má internímu problému. Tuto chybu mohl způsobit chyb v aplikaci nebo chyby v add-in nebo rozšíření, které používá.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** odebrat, opravit nebo znovu nainstalovat všechny rozšíření nebo doplňky.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 Tato Diagnostika Určuje, že byly během zámek zavaděče spouštění MSIL pokyny. Tato situace může nastat, pokud jste sestavili nativní C++ pomocí příznaku/CLR. Příznak/CLR lze použijte pouze na moduly, které obsahují spravovaného kódu. Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).