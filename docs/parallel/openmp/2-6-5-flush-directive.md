---
title: "2.6.5 flush – direktiva | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1911efe811545c13e62ab9f917ddfc284af35b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="265-flush-directive"></a>2.6.5 flush – direktiva
**Vyprázdnění** – direktiva, ať už explicitní nebo implicitní, určuje bod sekvence "mezi vlákny", kdy je potřeba zajistit, aby měly všechny vlákna v týmu konzistentní zobrazení určité objekty (uvedené níže) v implementaci paměť. To znamená, že předchozí vyhodnocení výrazů, které odkazují na tyto objekty dokončení a následné hodnocení není zahájeno. Například kompilátory musí obnovení hodnot objektů z registrů v paměti a hardwaru pravděpodobně muset vyprázdnění zápis vyrovnávací paměti do paměti a znovu načíst hodnoty objekty z paměti.  
  
 Syntaxe **vyprázdnění** – Direktiva vypadá takto:  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 Pokud objekty, které vyžadují synchronizaci můžete všechny označí proměnné, pak tyto proměnné lze zadat v nepovinný *seznamu proměnné*. Pokud je k dispozici v ukazatel *seznamu proměnné*ukazatele samotné vyprazdňuje, není objekt ukazatele odkazuje na.  
  
 A **vyprázdnění** direktiv bez *seznamu proměnné* synchronizuje všechny sdílené objekty s výjimkou nepřístupné objekty s dobou trvání automatické úložiště. (Toto je pravděpodobně další režii než **vyprázdnění** s *seznamu proměnné*.) A **vyprázdnění** direktiv bez *seznamu proměnné* je implicitní pro následující direktivy:  
  
-   `barrier`  
  
-   Na vstupu a výstupu z **kritické**  
  
-   Na vstupu a výstupu z`ordered`  
  
-   Na vstupu a výstupu z **paralelní**  
  
-   Na ukončit **pro**  
  
-   Na ukončit **části**  
  
-   Na ukončit **jeden**  
  
-   Na vstupu a výstupu z **paralelní pro**  
  
-   Na vstupu a výstupu z **parallel sections –**  
  
 Direktiva není implicitní, pokud `nowait` klauzule je k dispozici. Je třeba poznamenat, který **vyprázdnění** – direktiva není implicitní pro některé z následujících:  
  
-   Vstup **pro**  
  
-   Na položku na nebo ukončení z **hlavní**  
  
-   Vstup **části**  
  
-   Vstup **jeden**  
  
 Odkaz, který přistupuje k hodnotu objektu s typem kvalifikovaný volatile chová jako kdyby nebyla **vyprázdnění** – direktiva zadání tento objekt v předchozím bodu sekvence. Odkaz, který změní hodnotu objektu s typem kvalifikovaný volatile chová jako kdyby nebyla **vyprázdnění** – direktiva zadání tento objekt v okamžiku následné pořadí.  
  
 Všimněte si, že **vyprázdnění** – direktiva nemá příkaz jazyka C jako součást jeho syntaxe, platí určitá omezení na jeho umístění v rámci programu. V tématu [příloha C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md) pro formální gramatika. Následující příklad znázorňuje tato omezení.  
  
```  
/* ERROR - The flush directive cannot be the immediate  
*          substatement of an if statement.  
*/  
if (x!=0)  
   #pragma omp flush (x)  
...  
  
/* OK - The flush directive is enclosed in a  
*      compound statement  
*/  
if (x!=0) {  
   #pragma omp flush (x)  
}  
```  
  
 Omezení **vyprázdnění** – direktiva jsou následující:  
  
-   Proměnné zadané v **vyprázdnění** – direktiva nesmí mít odkazového typu.