---
title: "Vytváření skriptů pro Registrátor ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5142d0f5e3ede3a7cdd51af0fc54964b1cecec14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-registrar-scripts"></a>Vytváření skripty registrátora
Skript registrátora poskytuje řízené daty, nikoli rozhraní API řízené, přístup k registru systému. Řízené daty přístup je obvykle efektivnější, protože trvá pouze jeden nebo dva řádky ve skriptu přidání klíče registru.  
  
 [Průvodce ovládacím prvkem ATL](../atl/reference/atl-control-wizard.md) automaticky vytvoří skript registrátora pro váš server COM. Tento skript můžete najít v souboru přidružené k objektu.  
  
 Registrátor ATL skriptovací stroj zpracovává vašeho registrátora skriptu v době běhu. ATL automaticky vyvolá skriptovací stroj během instalace serveru.  
  
 Tento článek obsahuje následující témata týkající se skripty registrátora:  
  
-   [Principy Backus Nauer formuláře (BNF) syntaxe](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [Principy analýzy stromů](../atl/understanding-parse-trees.md)  
  
-   [Příklady skriptování registru](../atl/registry-scripting-examples.md)  
  
-   [Pomocí nahraditelné parametry (vašeho registrátora Preprocessor)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [Vyvolání skripty](../atl/invoking-scripts.md)  
  
## <a name="see-also"></a>Viz také  
 [Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)

