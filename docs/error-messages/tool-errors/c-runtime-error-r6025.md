---
title: Chyba v běhu R6025 C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6025
dev_langs:
- C++
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abdbdbf918462dfb83eff07190c32af1f1b3d015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6025"></a>R6025 Chyba za běhu C
volání čistý virtuální funkce  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má internímu problému. Nejčastější příčinou této chyby je chyb v aplikaci nebo poškozená instalace.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 Žádný objekt po vytvoření instance, zpracování volání čistý virtuální funkce.  
  
 Tato chyba je způsobená volání virtuální funkce v abstraktní základní třídu prostřednictvím ukazatele, který byl vytvořený přetypování na typ odvozené třídy, ale je ve skutečnosti ukazatel na základní třídy. Tato situace může nastat, když přetypování z **void\***  na ukazatel na třídu, když **void\***  byl vytvořen během vytváření základní třídy.  
  
 Další informace najdete v tématu [podporu společnosti Microsoft](http://go.microsoft.com/fwlink/p/?linkid=75220) webu.