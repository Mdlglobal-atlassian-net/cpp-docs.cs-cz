---
title: Průvodce třídou MFC
ms.date: 11/04/2016
f1_keywords:
- vc.wizards.classwizard
helpviewer_keywords:
- wizards (MFC)
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
ms.openlocfilehash: 59f0b39afe467267d61d7b851e654cc8bddc7b36
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265961"
---
# <a name="mfc-class-wizard"></a>Průvodce třídou MFC

Umožňuje přidat zprávy a obslužné rutiny zpráv na třídy v projektu. Můžete také spustit další průvodce nebo přidání třídy do projektu.

Chcete-li otevřít **Průvodce třídami MFC**na **projektu** nabídky, klikněte na tlačítko **Průvodce třídami**. Chcete-li průvodce spustit pomocí klávesové zkratky, stiskněte klávesy CTRL+SHIFT+X.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Projekt**

   Název projektu v rámci vašeho řešení.

   V řešení lze zvolit jiné projekty z rozevíracího seznamu.

- **Název třídy**

   Název třídy ve vašem projektu.

   Pokud vyberete třídu v **název třídy** seznamu, data ze třídy naplní ovládací prvky **Průvodce třídami MFC**. Při změně hodnoty ovládacího prvku je data ve třídě vybrané ovlivněna.

- **Přidat třídu**

   Umožňuje přidat třídu z jednoho z několika zdrojů.

   V závislosti na vašem výběru **Průvodce přidáním třídy MFC**, **přidání třídy z Průvodce knihovnou typů**, **třídy z ActiveX Průvodce přidáním ovládacího prvku**, nebo **knihovny MFC rozhraní ODBC Průvodce příjemcem** spuštění.

- **Základní třída**

   K základní třídě této třídy, která se zobrazí v **název třídy**.

- **Deklarace třídy**

   Třídy, ve které **název třídy** třída je deklarována.

   **Deklarace třídy** pole se zobrazí pouze v případě, že název v ní se liší od názvu v **implementace třídy**.

- **Prostředek**

   ID prostředku v **název třídy**, pokud nějaké existují. V opačném případě **prostředků** pole je prázdné.

- **Implementace třídy**

   Název souboru, který obsahuje implementaci třídy v **název třídy**.

   Kliknutím na šipku, můžete vybrat různé implementační soubor. V následující tabulce jsou uvedeny dostupné možnosti.

   |Možnost|Popis|
   |------------|-----------------|
   |**Otevřít soubor**|Ukončí průvodce třídami a otevře soubor implementace aktuální třídy.|
   |**Otevřít nadřazenou složku**|Otevře složku obsahující soubor implementace aktuální třídy.|
   |**Kopírovat úplnou cestu do schránky**|Cesta aktuální implementační soubor zkopíruje do schránky.|

- **Příkazy**

   Umožňuje přidat, odstranit, upravit nebo vyhledání příkazu a jeho obslužné rutiny zpráv.

   Chcete-li přidat obslužnou rutinu, klikněte na tlačítko **přidat obslužnou rutinu**, nebo dvakrát klikněte na položku v **ID objektů** seznamu nebo **zprávy** seznamu. Výsledný název funkce, ID a zpráva se zobrazí v **členské funkce** seznamu.

   Pokud chcete odstranit obslužnou rutinu, zvolit položku v **členské funkce** seznamu a potom klikněte na **odstranit obslužnou rutinu**.

   Chcete-li změnit obslužnou rutinu, dvakrát klikněte na odpovídající položku v **členské funkce** seznamu. Nebo, v seznamu vyberte položku a pak klikněte na tlačítko **upravit kód**.

- **Zprávy**

   Umožňuje přidat, odstranit, upravit nebo vyhledejte zprávu a její obslužná rutina zprávy.

   Chcete-li přidat obslužnou rutinu, klikněte na tlačítko **přidat obslužnou rutinu**, nebo dvakrát klikněte na položku v **zprávy** seznamu.

   Chcete-li přidat vlastní zprávu, klikněte na tlačítko **přidat vlastní zprávu** nebo stiskněte klávesu Enter a poté zadejte hodnoty v **přidat vlastní zprávu** dialogové okno. V tomto dialogovém okně můžete také vybrat **registrovanou zprávu** zpracovat zprávu okna, která je zaručeně jedinečná v celém operačním systému.

- **Virtuální funkce**

   Umožňuje přidat, odstranit, upravit nebo vyhledejte virtuální funkci nebo přepsané virtuální funkce.

- **Členské proměnné**

   Umožňuje přidat, odstranit, upravit nebo vyhledejte členské proměnné.

- **Metody**

   Umožňuje přidat, odstranit, nebo vyhledejte metodu a také myší přejít na definice nebo deklarace metody.

   Přidání metody, klikněte na tlačítko **přidat metodu**a poté zadejte hodnoty v **přidat metodu** dialogové okno.

   Pokud chcete metodu odstranit, vyberte položku v **metody** seznamu a potom klikněte na tlačítko **metodu Delete**.

   Chcete-li zobrazit prohlášení, zvolit položku v **metody** seznamu a potom klikněte na tlačítko **přejít na deklaraci.**

   Chcete-li zobrazit definici, dvakrát klikněte na položku **metody** seznamu. Nebo vyberte položku **metody** seznamu a potom klikněte na tlačítko **přejít k definici** tlačítko.

## <a name="see-also"></a>Viz také:

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)
