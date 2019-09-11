---
title: Průvodce třídou MFC
ms.date: 09/06/2019
f1_keywords:
- vc.wizards.classwizard
helpviewer_keywords:
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
ms.openlocfilehash: be829156d8fea8188a217b2c0a189ac5d6057a7e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908006"
---
# <a name="mfc-class-wizard"></a>Průvodce třídou MFC

Pomocí **Průvodce třídami** můžete vytvořit nové třídy knihovny MFC nebo přidat zprávy a obslužné rutiny zpráv do existujících tříd v projektu.

Existují tři způsoby, jak otevřít **Průvodce třídami**:

- V nabídce **projekt** klikněte na příkaz **Průvodce třídami**.
- Zadejte **CTRL** > ShiftX > .
- V **zobrazení tříd**klikněte pravým tlačítkem myši na třídu nebo na uzel projektu a vyberte možnost **Průvodce třídami**.

![Průvodce třídami](media/class-wizard.png "Průvodce třídou MFC")

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Projekt**

   Název projektu ve vašem řešení.

   V řešení lze zvolit jiné projekty z rozevíracího seznamu.

- **Název třídy**

   Název třídy v projektu.

   Když vyberete třídu v seznamu **název třídy** , data z třídy naplní ovládací prvky v **Průvodci třídou knihovny MFC**. Při změně hodnoty ovládacího prvku jsou ovlivněna data ve vybrané třídě.

- **Přidat třídu**

   Umožňuje přidat novou třídu do projektu knihovny MFC.

- **Základní třída**

   Základní třída třídy, která je zobrazena v **názvu třídy**.

- **Deklarace třídy**

   Třída, ve které je deklarována třída **názvu třídy** .

   Pole **deklarace třídy** se zobrazí pouze v případě, že se název v něm liší od názvu v **implementaci třídy**.

- **Prostředek**

   ID prostředku v **názvu třídy**, pokud existuje. V opačném případě je pole **prostředku** prázdné.

- **Implementace třídy**

   Název souboru, který obsahuje implementaci třídy v **názvu třídy**.

   Kliknutím na šipku můžete vybrat jiný implementační soubor. V následující tabulce jsou uvedeny dostupné možnosti.

   |Možnost|Popis|
   |------------|-----------------|
   |**Otevřít soubor**|Ukončí průvodce třídami a otevře soubor implementace aktuální třídy.|
   |**Otevřít nadřazenou složku**|Otevře složku, která obsahuje aktuální soubor implementace třídy.|
   |**Kopírovat úplnou cestu do schránky**|Zkopíruje cestu k aktuálnímu implementačnímu souboru do schránky.|

- **Příkaz**

   Umožňuje přidat, odstranit, upravit nebo vyhledat příkaz a jeho obslužnou rutinu zprávy.

   Chcete-li přidat obslužnou rutinu, klikněte na tlačítko **Přidat obslužnou rutinu**nebo dvakrát klikněte na položku v seznamu **ID objektů** nebo seznam **zpráv** . Výsledný název funkce, ID a zpráva se zobrazí v seznamu **členské funkce** .

   Chcete-li odstranit obslužnou rutinu, vyberte položku v seznamu **členské funkce** a pak klikněte na tlačítko **odstranit obslužnou rutinu**.

   Chcete-li změnit obslužnou rutinu, dvakrát klikněte na odpovídající položku v seznamu **členské funkce** . Případně vyberte položku v seznamu a klikněte na tlačítko **Upravit kód**.

- **Zprávy**

   Umožňuje přidat, odstranit, upravit nebo vyhledat zprávu a její obslužnou rutinu zprávy.

   Chcete-li přidat obslužnou rutinu, klikněte na tlačítko **Přidat obslužnou rutinu**nebo dvakrát klikněte na položku v seznamu **zpráv** .

   Chcete-li přidat vlastní zprávu, klikněte na tlačítko **Přidat vlastní zprávu** nebo stiskněte klávesu ENTER a zadejte hodnoty do dialogového okna **Přidat vlastní zprávu** . V tomto dialogovém okně můžete také vybrat **zaregistrovanou zprávu** pro zpracování zprávy okna, u které je zaručeno, že bude v celém operačním systému jedinečný.

- **Virtuální funkce**

   Umožňuje přidat, odstranit, upravit nebo vyhledat virtuální funkci nebo přepsanou virtuální funkci.

- **Proměnné členů**

   Umožňuje přidat, odstranit, upravit nebo vyhledat členskou proměnnou.

- **Metody**

   Umožňuje přidat, odstranit nebo vyhledat metodu a také přejít na definici nebo deklaraci metody.

   Chcete-li přidat metodu, klikněte na tlačítko **Přidat metodu**a pak zadejte hodnoty do dialogového okna **Přidat metodu** .

   Chcete-li odstranit metodu, vyberte položku v seznamu **metody** a pak klikněte na tlačítko **Odstranit metodu**.

   Chcete-li zobrazit deklaraci, vyberte položku v seznamu **metody** a pak klikněte na tlačítko **Přejít k deklaraci.**

   Chcete-li zobrazit definici, dvakrát klikněte na položku v seznamu **metody** . Případně vyberte položku v seznamu **metody** a pak klikněte na tlačítko **Přejít k definici** .

## <a name="see-also"></a>Viz také:

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)
