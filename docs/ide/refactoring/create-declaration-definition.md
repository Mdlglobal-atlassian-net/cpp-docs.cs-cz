---
title: Vytvoření deklarace nebo definice | Microsoft Docs
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
ms.openlocfilehash: 60d583ec47a3f9c5b61599a5945e3cfa0d375b1d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33331280"
---
# <a name="create-declaration--definition"></a>Vytvoření deklarace nebo definice
**Co:** umožňuje okamžitě generovat deklarace a definice funkce.

**Kdy:** máte funkci, která vyžaduje přijato prohlášení nebo naopak.  

**Důvod:** můžete ručně vytvořit deklarací a definic, ale tím se vytvoří se automaticky, vytvoření souboru záhlaví/kódu v případě potřeby.

**Postupy:**

1. Umístěte kurzor text nebo myši nad funkce, pro který chcete vytvořit deklarace a definice.

   ![Zvýrazněný kód](images/createdefinition_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stiskněte klávesu **Ctrl +.** k aktivační události **rychlé akce a refaktoring** nabídku a vyberte **vytvořit deklarace nebo definice** v místní nabídce.
   * **Myš**
     * Klikněte pravým tlačítkem a vyberte **rychlé akce a refaktoring** nabídku a vyberte **vytvořit deklarace nebo definice** v místní nabídce.

1. Deklarace nebo definici funkcí budou vytvořeny v zdroje nebo hlavičce souboru, který se zobrazí v automaticky otevřeném okně okně preview.  Pokud zdroj nebo hlavičce soubor neexistuje, bude také vytvořit a umístit do projektu.

   ![Vytvořit deklaraci / způsobit definice](images/createdefinition_result.png)
