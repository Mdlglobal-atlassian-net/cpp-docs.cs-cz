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
ms.workload: cplusplus
ms.openlocfilehash: b3bda4043693d14451a2de14cbc71fbecdcdddba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-registrar-scripts"></a>Vytváření skripty registrátora
Skript registrátora poskytuje řízené daty, nikoli rozhraní API řízené, přístup k registru systému. Řízené daty přístup je obvykle efektivnější, protože trvá pouze jeden nebo dva řádky ve skriptu přidání klíče registru.  
  
 [Průvodce ovládacím prvkem ATL](../atl/reference/atl-control-wizard.md) automaticky vytvoří skript registrátora pro váš server COM. Tento skript můžete najít v souboru přidružené k objektu.  
  
 Registrátor ATL skriptovací stroj zpracovává vašeho registrátora skriptu v době běhu. ATL automaticky vyvolá skriptovací stroj během instalace serveru.  
  
 Tento článek obsahuje následující témata týkající se skripty registrátora:  
  
-   [Principy syntaxe BNF (Backus Nauer Form)](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [Principy stromů analýzy](../atl/understanding-parse-trees.md)  
  
-   [Příklady skriptování registru](../atl/registry-scripting-examples.md)  
  
-   [Použití nahraditelných parametrů (preprocesor registrátoru)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [Volání skriptů](../atl/invoking-scripts.md)  
  
## <a name="see-also"></a>Viz také  
 [Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)

