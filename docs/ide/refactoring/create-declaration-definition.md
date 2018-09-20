---
title: Vytvořit deklaraci / definici | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 383691a5c2da2af6e4a992ab8766cd99ffa3d781
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408385"
---
# <a name="create-declaration--definition"></a>Vytvořit deklaraci / definici
**Co:** umožňuje okamžitě generovat deklarace nebo definice funkce.

**Kdy:** máte funkci, která potřebuje přijato prohlášení nebo naopak.

**Důvod, proč:** můžete ručně vytvořit deklaraci/definici, ale tím se vytvoří jej automaticky, v případě potřeby vytvoření záhlaví/kódový soubor.

**Jak:**

1. Umístěte ukazatel myši text nebo myši nad funkce, pro které chcete k vytvoření deklarace nebo definice.

   ![Zvýrazněný kód](images/createdefinition_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stisknutím klávesy **Ctrl +.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **vytvořit deklaraci / definici** v místní nabídce.
   * **Myši**
     * Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **vytvořit deklaraci / definici** v místní nabídce.

1. Deklarace/definice funkce se vytvoří ve zdrojové nebo záhlaví souboru, který se zobrazí v automaticky otevíraném okně ve verzi preview.  Pokud zdroj nebo záhlaví souboru neexistuje, bude také vytvořena a umístěna do projektu.

   ![Vytvořit deklaraci / definici způsobit](images/createdefinition_result.png)
