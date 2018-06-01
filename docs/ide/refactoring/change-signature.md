---
title: Změnit podpis | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f913f0b3065b136f626ef15cc2a77dce8d0254f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33335088"
---
# <a name="change-signature"></a>Změna podpisu
**Co:** umožňuje upravit parametry funkce.

**Kdy:** chcete změnit pořadí, přidat, odebrat nebo změnit parametry funkce, které se aktuálně používá v různých umístěních.  

**Důvod:** může ručně změnit tyto parametry sami a potom najít všechna volání této funkce a jejich změnu jeden po druhém, ale které může vést k chybám.  Tento nástroj refaktoringu automaticky provede úlohu.

**Postupy:**

1. Umístěte kurzor text nebo myš do název metody k úpravě nebo jeden z jeho použití:

   ![Zvýrazněný kód](images/changesignature_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stiskněte klávesu **Ctrl + R**, pak **Ctrl + O**.  (Všimněte si, že klávesové zkratky se může lišit na základě na profilu, které jste vybrali.)
     * Stiskněte klávesu **Ctrl +.** k aktivační události **rychlé akce a refaktoring** nabídku a vyberte **změnu podpis** v místní nabídce.
   * **Myš**
     * Vyberte **Upravit > Refaktorovat > přeskupení parametrů**.
     * Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a refaktoring** nabídku a vyberte **změnu podpis** v místní nabídce.

1. V **změnit podpis** dialogové okno, která se objeví, změníte podpis metody můžete pomocí tlačítek na pravé straně:

   ![Dialogové okno změnit podpis](images/changesignature_dialog.png)

   | Tlačítko | Popis
   | ------ | ---
   | **Nahoru/dolů**    | Přesunout vybraný parametr nahoru a dolů v seznamu
   | **Přidat**        | Přidat nový parametr do seznamu
   | **Odebrat**     | Odeberte parametr vybraný ze seznamu
   | **Upravit**     | Upravte vybraný parametr tak, že změníte typ, název a jestli je volitelná a co by jeho vloženého hodnota
   | **Vrátit zpět**     | Vybraný parametr obnovení původního stavu
   | **Vraťte zpátky všechny** | Obnovit všechny parametry do původního stavu

   > [!TIP]
   > Použití **přeskočit preview odkaz změny, pokud byly potvrzeny všechny odkazy** zaškrtávací políčko k provádění změn okamžitě bez okno náhledu automaticky objevují na první obrazovce.

   Při přidávání nebo úpravě parametr, zobrazí se **přidat parametr** nebo **upravit parametr** okno.

   ![Přidat nebo změnit parametr](images/changesignature_addmodify.png)

   Zde můžete provést následující:

   | Položka | Popis
   | ----- | ---
   | **Typ**               | Typ parametru (int, dvakrát, float, atd.)
   | **Jméno**               | Název parametru
   | **Volitelný parametr** | Umožňuje volitelně zadat parametr
   | **Vložený hodnota**     | Hodnota vložená do jakékoli volání funkce tam, kde není zadán parametr (platné pouze pro **přidat**)
   | **Výchozí hodnota**      | Používat funkci, pokud má volající není zadejte jednu hodnotu (platné pouze pro **volitelné parametry**)

1. Použití **obor vyhledávání** rozevírací nabídku a vyberte, pokud změny se použijí na projekt nebo celé řešení.

1. Když skončíte, stiskněte **OK** tlačítko provést změny.  Ujistěte se, že změny, které jste požádali se provádějí správně.  Pomocí zaškrtávacích políček k povolení nebo zakázání přejmenování libovolnou položku v horní polovině okna.

   ![Změnit podpis preview](images/changesignature_preview.png)

1. Pokud se vše spokojeni, klikněte na tlačítko **použít** tlačítko a funkce se změní ve zdrojovém kódu.

   ![Podpis výsledek změny](images/changesignature_result.png)