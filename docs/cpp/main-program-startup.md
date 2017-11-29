---
title: "hlavní: spuštění programu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc.main.startup
- _tmain
dev_langs: C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- wmain function
- _tmain function
- startup code, main function
- main function, program startup
ms.assetid: f9581cd6-93f7-4bcd-99ec-d07c3c107dd4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 37b08b5108d609deca2eed94a05d4eb01d09f10b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="main-program-startup"></a>main: nastavení programu
Speciální funkce s názvem `main` je výchozí bod spuštění pro všechny programy C a C++. Pokud jste psaní kódu, který dodržuje [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] programovací model, můžete použít `wmain`, což je verze široká charakterová `main`.  
  
 `main` Kompilátorem není předdefinované funkce. Je potřeba zadat ve text programu.  
  
 Syntaxe deklarace pro `main` je  
  
```  
int main();  
```  
  
 případně  
  
```  
int main(int argc, char *argv[], char *envp[]);  
```  
  
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Syntaxe deklarace pro `wmain` vypadá takto:  
  
```  
int wmain( );  
```  
  
 případně  
  
```  
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);  
```  
  
 Můžete také použít `_tmain`, který je definován v souboru TCHAR.h. `_tmain`přeloží na `main` Pokud _UNICODE je definována. V takovém případě `_tmain` přeloží na `wmain`.  
  
 Případně `main` a `wmain` funkce lze deklarovat jako vrácení `void` (žádnou návratovou hodnotu). Pokud je deklarovat `main` nebo `wmain` jako vrácení `void`, ukončovací kód nelze vrátit k nadřazeného procesu nebo operačního systému pomocí [vrátit](../cpp/return-statement-in-program-termination-cpp.md) příkaz. Vrátit ukončovací kód při `main` nebo `wmain` je deklarován jako `void`, je nutné použít [ukončete](../cpp/exit-function.md) funkce.  
  
**Konkrétní Microsoft END**  
 Typy pro `argc` a `argv` jsou definovány pomocí jazyka. Názvy `argc`, `argv`, a `envp` jsou tradiční, ale nejsou požadována kompilátoru. Další informace a příklady naleznete v tématu [definice argumentů](../cpp/argument-definitions.md).  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Použití funkce wmain namísto main](../cpp/using-wmain-instead-of-main.md)   
 [Main – omezení funkce](../cpp/main-function-restrictions.md)