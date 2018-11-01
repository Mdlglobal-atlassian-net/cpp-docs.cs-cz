---
title: Změnit signaturu
ms.date: 11/16/2016
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
ms.openlocfilehash: 776f777eb64128e9914e6d087551930593a490fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584038"
---
# <a name="change-signature"></a>Změnit signaturu
**Co:** umožňuje změnit parametry funkce.

**Kdy:** chcete přeuspořádat, přidat, odebrat nebo změnit parametry funkce, které se aktuálně používá v různých umístěních.

**Důvod, proč:** můžete ručně tyto parametry měnit sami a poté najít všechny volání této funkce a je změnit jednu po druhé, ale které by mohly vést k chybám.  Tento refaktoring nástroj automaticky provede úlohu.

**Jak:**

1. Umístěte kurzor text nebo myši mezi název metody, která upravit, nebo jedno z jeho použití:

   ![Zvýrazněný kód](images/changesignature_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Klávesnice**
     * Stisknutím klávesy **Ctrl + R**, pak **Ctrl + O**.  (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
     * Stisknutím klávesy **Ctrl +.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **změnit signaturu** v místní nabídce.
   * **Myši**
     * Vyberte **Upravit > Refaktorovat > přeskupení parametrů**.
     * Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **změnit signaturu** v místní nabídce.

1. V **změnit podpis** dialogového okna, která se otevře, můžete změnit podpis metody můžete pomocí tlačítka na pravé straně:

   ![Změnit podpis dialogového okna](images/changesignature_dialog.png)

   | Tlačítko | Popis
   | ------ | ---
   | **Směrem nahoru nebo dolů**    | Přesunout vybraný parametr nahoru a dolů v seznamu
   | **Add**        | Přidání nových parametrů do seznamu
   | **odebrat**     | Odebrat vybraný parametr ze seznamu
   | **Upravit**     | Upravit vybraný parametr tak, že změníte její typ, název a určuje, zda je volitelné a co by byla hodnotou vloženého
   | **Vrátit zpět**     | Obnovení původního stavu vybraný parametr
   | **Vraťte zpátky všechny** | Obnovit všechny parametry do původního stavu

   > [!TIP]
   > Použití **přeskočit náhledu odkazu změní, pokud jsou všechny odkazy potvrzené** zaškrtávací políčko okamžitě provést změny bez nezobrazuje první okno náhledu.

   Když přidáváte nebo měníte parametr, zobrazí se **přidat parametr** nebo **upravit parametr** okna.

   ![Přidat nebo upravit parametr](images/changesignature_addmodify.png)

   Tady můžete postupujte takto:

   | Položka | Popis
   | ----- | ---
   | **Typ**               | Typ parametru (int, dvakrát, float, atd.)
   | **Jméno**               | Název parametru
   | **Volitelný parametr** | Umožňuje zadat parametr
   | **Vložená hodnota**     | Hodnota vložená do volání funkce, pokud není zadán parametr (platné pouze pro **přidat**)
   | **Výchozí hodnota**      | Používá funkce, pokud volající nemá určenou jednu hodnotu (platné pouze pro **volitelné parametry**)

1. Použití **obor vyhledávání** rozevírací seznam a vyberte, pokud změny platit pro projekt nebo celé řešení.

1. Až skončíte, stiskněte **OK** tlačítko provést změny.  Ujistěte se, že změny, které jste požádali se provádějí odpovídajícím způsobem.  K povolení nebo zakázání přejmenování libovolnou položku pomocí zaškrtávacích políček v horní části okna.

   ![Změnit podpis ve verzi preview](images/changesignature_preview.png)

1. Pokud vše vypadá v pořádku, klikněte na tlačítko **použít** tlačítko a funkce se změní ve zdrojovém kódu.

   ![Podpis výsledek změny](images/changesignature_result.png)