---
title: Přesunout umístění definice | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5058e0b3bab1fb5fb5e8d52b55e3fa7c37fd8a4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430042"
---
# <a name="move-definition-location"></a>Přesunout umístění definice
**Co:** umožňuje okamžitě přesunutí definice funkce pro odpovídající soubor záhlaví.

**Kdy:** máte funkci, kterou chcete přesunout do souboru hlaviček.

**Důvod, proč:** můžete ručně přesunout funkci, ale tato funkce se jej přesunout automaticky, vytváření souboru hlaviček v případě potřeby.

**Jak:**

1. Umístěte ukazatel myši text nebo myši nad funkce, pro který chcete přesunout.

   ![Zvýrazněný kód](images/movedefinition_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stisknutím klávesy **Ctrl +.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **přesunout umístění definice** v místní nabídce.
   * **Myši**
     * Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **přesunout umístění definice** v místní nabídce.

1. Funkce se přesunou na odpovídající soubor záhlaví, která se zobrazí v automaticky otevíraném okně ve verzi preview.  Pokud hlavičkový soubor buď neexistuje, bude také vytvořena a umístěna do projektu.

   ![Vytvořit deklaraci / definici způsobit](images/movedefinition_result.png)
