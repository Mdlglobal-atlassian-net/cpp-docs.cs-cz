---
title: "Chyba v běhu R6031 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6031
dev_langs: C++
helpviewer_keywords: R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 587b370e94de573f262772de0f5a8bf34f25124b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6031"></a>R6031 Chyba za běhu C
Pokus o inicializaci CRT více než jednou. To znamená chyb v aplikaci.  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má internímu problému. To může být způsobeno chyb v aplikaci, nebo chyby v rozšíření nebo rozšíření, které aplikace používá.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** odebrat, opravit nebo znovu nainstalovat všechny programy rozšíření nebo rozšíření používané aplikace.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 Tato Diagnostika Určuje, že byly během zámek zavaděče spouštění MSIL pokyny. Další informace najdete v tématu [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).