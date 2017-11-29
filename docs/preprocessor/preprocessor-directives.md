---
title: "Preprocesor – direktivy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 105155a601a062baaebc0abbb1a7dfe23f33b78e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="preprocessor-directives"></a>Preprocesor – direktivy
Preprocesor – direktivy, jako například `#define` a **#ifdef**, jsou obvykle používány k vytvoření zdrojové programy snadno změnit a snadno zkompilovat v jiném pracovním prostředí. Direktivy ve zdrojovém souboru řekněte preprocesor provedení určitých akcí. Preprocesor můžete například nahradit tokeny v textu, vložte obsah dalších souborů do zdrojového souboru nebo potlačit kompilace část souboru, odebráním části textu. Preprocesoru řádky jsou rozpoznána a provádějí před makro rozšíření. Proto pokud makra rozšíří na objekt, který vypadá jako preprocesoru příkaz, tento příkaz nebyl rozpoznán balíčkem preprocesor.  
  
 Preprocesor – příkazy použít stejný znak nastavit jako zdrojový soubor příkazy, s tím rozdílem, že řídicí sekvence nejsou podporovány. Znakové sady použité v příkazech preprocesoru je stejný jako [znaková sada spuštění](http://msdn.microsoft.com/en-us/a7901c61-524d-47c6-beb6-d9dacc2e72ed). Preprocesor také rozpoznává záporné znakových hodnot.  
  
 Preprocesor rozpoznává následující direktivy:  
  
|||||  
|-|-|-|-|  
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|  
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|  
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|  
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||  
  
 Znaménko čísla (**#**) musí být první znak neprázdný na řádek obsahující – direktiva; mezi znaménko čísla a první písmeno direktiva může vyskytovat prázdné znaky. Některé direktivy zahrnují argumentů nebo hodnoty. Text, který následuje – direktiva (s výjimkou argument nebo hodnotu, která je součástí direktiva) musí předcházet oddělovač jednořádkový komentář (**//**) nebo uzavřena v oddělovače komentářů ( **/ \* \*/**). Řádky se direktivy preprocesoru lze pokračovat tak, že bezprostředně před značku konec řádku obráceným lomítkem (**\\**).  
  
 Preprocesor – direktivy může vyskytovat kdekoli v zdrojový soubor, ale se vztahují pouze na zbytek zdrojový soubor.  
  
## <a name="see-also"></a>Viz také  
 [Operátory preprocesoru](../preprocessor/preprocessor-operators.md)   
 [Předdefinovaná makra](../preprocessor/predefined-macros.md)   
 [C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)