---
title: "2.7.2.1 privátní | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a08faf39ab2f82d76a936c216ba6707bee5c240
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="2721-private"></a>2.7.2.1 private
`private` Klauzule jsou proměnné deklarovány v seznamu proměnné důvěrné každé vlákno v týmu. Syntaxe `private` klauzule vypadá takto:  
  
```  
private(variable-list)  
```  
  
 Chování proměnné zadané v `private` klauzule je následující. Vytvoření nového objektu s dobou trvání automatické úložiště přidělené konstrukce. Typ proměnné určuje velikost a zarovnání nového objektu. Toto přidělení akce proběhne jednou pro každé vlákno v týmu a výchozí konstruktor je volána pro objekt třídy v případě potřeby; v opačném případě je počáteční hodnota neurčitou.  Původní objekt odkazuje proměnná má hodnotu neurčitém při vstupu do konstruktu, nesmí být upraveno v rámci dynamické rozsah konstruktu a má neurčitém hodnotu po opuštění konstruktu.  
  
 Lexikální rozsahu direktivy konstrukce odkazuje proměnná nový soukromý objekt přidělena vlákno.  
  
 Omezení, které mají `private` klauzule jsou následující:  
  
-   Proměnná s typu třídy, který je uveden v `private` klauzule musí mít k přístupný, jednoznačným výchozí konstruktor.  
  
-   Proměnné zadané v `private` nesmí mít klauzuli **const**-kvalifikovaný typ, pouze pokud má třídu, zadejte s `mutable` člen.  
  
-   Zadaný v proměnné `private` klauzule nesmí mít typ neúplné nebo typu odkazu.  
  
-   Proměnné, které se zobrazují v `reduction` klauzuli **paralelní** – direktiva nelze zadat v `private` klauzule ve sdílení práce direktiva, která se sváže s paralelní konstrukce.