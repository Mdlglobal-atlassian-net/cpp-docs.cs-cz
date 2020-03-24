---
title: Změnit signaturu
ms.date: 11/16/2016
ms.assetid: 8daaa060-7305-4035-99d2-8b460b4f4454
ms.openlocfilehash: 1599a7900e33db61994ea75581f9d87b1aee83f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171902"
---
# <a name="change-signature"></a>Změnit signaturu

**Co:** Umožňuje upravit parametry funkce.

**Když:** Chcete změnit pořadí, přidání, odebrání nebo úpravu parametrů funkce, které jsou aktuálně používány v různých umístěních.

**Proč:** Tyto parametry můžete ručně změnit sami a pak vyhledat všechna volání této funkce a změnit je po jednom, ale to může vést k chybám.  Tento refaktoring nástroj automaticky provede úlohu.

**Použití**

1. Umístěte text nebo kurzor myši do názvu metody, kterou chcete změnit, nebo jedno z jeho použití:

   ![Zvýrazněný kód](images/changesignature_highlight.png)

1. Dále proveďte jednu z následujících akcí:
   * **Kombinace**
     * Stiskněte klávesy **CTRL + R**a pak **kombinaci kláves CTRL + O**.  (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
     * Stiskněte **kombinaci kláves CTRL +.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v místní nabídce vyberte možnost **změnit podpis** .
   * **Stisknut**
     * Vyberte možnost **upravit > refaktoring > změnit pořadí parametrů**.
     * Klikněte pravým tlačítkem na kód, vyberte nabídku **rychlé akce a refaktoring** a v místní nabídce vyberte **změnit signaturu** .

1. V dialogu **změnit podpis** , který se zobrazí, můžete pomocí tlačítek na pravé straně změnit signaturu metody:

   ![Změnit podpis dialogového okna](images/changesignature_dialog.png)

   | Tlačítko | Popis
   | ------ | ---
   | **Nahoru/dolů**    | Přesunout vybraný parametr nahoru a dolů v seznamu
   | **Add**        | Přidat do seznamu nový parametr
   | **Odebrány**     | Odebrat vybraný parametr ze seznamu
   | **Upravíte**     | Upravte vybraný parametr změnou jeho typu, názvu a toho, zda je volitelný a jak by byla vložená hodnota.
   | **Stane**     | Obnovit vybraný parametr do původního stavu
   | **Vrátit vše** | Obnoví všechny parametry do původního stavu.

   > [!TIP]
   > Zaškrtnutím políčka **Přeskočit náhled změn odkazů, pokud jsou všechny odkazy potvrzené** , provedete změny hned bez předchozího odebrání okna náhledu.

   Když přidáváte nebo upravujete parametr, zobrazí se okno **Přidat parametr** nebo **Upravit parametr** .

   ![Přidat/změnit parametr](images/changesignature_addmodify.png)

   Tady můžete postupovat takto:

   | Záznam | Popis
   | ----- | ---
   | **Typ**               | Typ parametru (int, Double, float atd.)
   | **Název**               | Název parametru
   | **Volitelný parametr** | Nastaví parametr volitelně jako zadaný.
   | **Vložená hodnota**     | Hodnota vložená do všech volání funkce, kde parametr není zadán (platný pouze pro **Přidání**)
   | **Výchozí hodnota**      | Hodnota, kterou funkce používá, pokud volající nezadá žádný (platný jenom pro **volitelné parametry**)

1. Pomocí rozevíracího seznamu **Rozsah hledání** můžete vybrat, jestli se změny budou vztahovat na projekt nebo celé řešení.

1. Po dokončení klikněte na tlačítko **OK** , aby se změny projevily.  Ujistěte se, že změny, které požadujete, jsou vhodně provedeny.  Pomocí zaškrtávacích políček v horní polovině okna povolíte nebo zakážete přejmenování libovolné položky.

   ![Změnit signaturu náhledu](images/changesignature_preview.png)

1. Pokud vše vypadá dobře, klikněte na tlačítko **použít** a funkce se změní ve zdrojovém kódu.

   ![Změnit výsledek podpisu](images/changesignature_result.png)
