---
title: Vytváření skriptů pro doménový Registrátor ATL | Dokumentace Microsoftu
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
ms.openlocfilehash: abffe3c8d0a107c48c3a14a9bf584122229ad3b7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767257"
---
# <a name="creating-registrar-scripts"></a>Vytváření skriptů registrátoru

Doménový Registrátor skript představuje řízené daty, spíše než rozhraní API řízené a přístup k registru systému. Přístup s daty je obvykle efektivnější, protože trvá pouze jeden nebo dva řádky ve skriptu pro přidání klíče registru.

[Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md) automaticky generuje registrátora skript pro váš server COM. Tento skript najdete v souboru .rgs přidružené k objektu.

Doménový Registrátor ATL skriptovací stroj zpracovává vašeho registrátora skriptu v době běhu. ATL – automaticky vyvolá skriptovací stroj během instalace serveru.

Tento článek obsahuje následující témata související s skripty registrátora:

- [Principy syntaxe BNF (Backus Nauer Form)](../atl/understanding-backus-nauer-form-bnf-syntax.md)

- [Principy stromů analýzy](../atl/understanding-parse-trees.md)

- [Příklady skriptování registru](../atl/registry-scripting-examples.md)

- [Použití nahraditelných parametrů (preprocesor registrátoru)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [Volání skriptů](../atl/invoking-scripts.md)

## <a name="see-also"></a>Viz také

[Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)

