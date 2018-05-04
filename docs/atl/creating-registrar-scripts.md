---
title: Vytváření skriptů pro Registrátor ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e140e66ee24d8333d25c0c2942924c7a9db4965b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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

