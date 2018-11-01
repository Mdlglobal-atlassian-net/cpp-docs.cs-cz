---
title: Přidání třídy z průvodce ovládacím prvkem ActiveX
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
ms.openlocfilehash: 736ac50f14d8434584c6f47b2953913c79b0b00a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472485"
---
# <a name="add-class-from-activex-control-wizard"></a>Přidání třídy z průvodce ovládacím prvkem ActiveX

Tohoto průvodce použijte k přidání třídy knihovny MFC z ovládacího prvku ActiveX k dispozici. Průvodce vytvoří třídu pro každé rozhraní, kterou přidáte z vybraného ovládacího prvku ActiveX.

- **Přidat třídu Z:**

   Určuje umístění knihovny typů, ze kterého se vytvoří třídu.

   |Možnost|Popis|
   |------------|-----------------|
   |**Registru**|Knihovna typů je registrován v systému. Zaregistrované knihovny typů jsou uvedeny v **dostupné ovládací prvky ActiveX**.|
   |**Soubor**|Knihovna typů není nutně registrován v systému, ale je obsažena v souboru. Je nutné zadat umístění souborů v **umístění**.|

- **Dostupné ovládací prvky ActiveX**

   Určuje ovládací prvky ActiveX, které jsou aktuálně registrované v systému. Vyberte ze seznamu zobrazíte jeho rozhraní v ovládacím prvku ActiveX **rozhraní** seznamu. Zobrazit [knihovny MFC – ovládací prvky ActiveX: distribuce ovládacích prvků ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) Další informace o registraci komponenty – ovládací prvky ActiveX.

   Vyberete-li **souboru** pod **přidat třídu z**, toto pole je k dispozici pro změnu.

- **Poloha**

   Určuje umístění ovládacího prvku ActiveX. Vyberete-li **souboru** pod **přidat třídu z**, můžete uvést umístění souboru, který obsahuje knihovnu typů. Přejděte do umístění souboru, klikněte na tlačítko se třemi tečkami.

   Vyberete-li **registru** pod **přidat třídu z**, toto pole je k dispozici pro změnu.

- **Rozhraní**

   Určuje ovládací prvek ActiveX, který je aktuálně vybrána v rozhraní **dostupné ovládací prvky ActiveX** nebo v knihovně typů v souboru zadaného v **umístění**.

   |Tlačítka převodu|Popis|
   |---------------------|-----------------|
   |**>**|Přidá rozhraní vybrané v **rozhraní** seznamu. Tato možnost je k dispozici, pokud není vybrané žádné rozhraní.|
   |**>>**|Přidá všechna rozhraní v aktuálně vybraného v ovládacím prvku ActiveX **dostupné ovládací prvky ActiveX** nebo v knihovně typů v souboru zadaného v **umístění**.|
   |**\<**|Odebere aktuálně vybranou v třídu **generované třídy** seznamu. Není k dispozici, pokud není žádná třída aktuálně vybraný **generované třídy** seznamu.|
   |**\<\<**|Odebere všechny třídy v **generované třídy** seznamu. Pokud není k dispozici **generované třídy** seznam je prázdný.|

- **Generované třídy**

   Určuje názvy tříd, které mají být vygenerovány z rozhraní přidaných pomocí **>** nebo **>>** tlačítko. Můžete kliknout na toto políčko, aby vyberte třídu a potom použít nahoru nebo dolů kláves procházejte seznam, název každé třídy v zobrazení `Class` a název souboru v **souboru .h** pole, které průvodce vygeneruje po kliknutí na  **Dokončit**. V tomto poli můžete vybrat pouze jednu třídu najednou.

   Třídu můžete odebrat tak, že ji vyberete v tomto seznamu a kliknete na **<**. Není potřeba vybrat třídu v **generované třídy** pole odebrat všechny třídy; kliknutím **<<**, odeberte všechny třídy v **generované třídy** pole.

- **Třída**

   Určuje název třídy vybraný v **generované třídy** pole, které průvodce přidá po kliknutí na **Dokončit**. Můžete upravit název v **třídy** pole.

- **soubor .h**

   Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **generované třídy**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud zvolíte existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **soubor .cpp**

   Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **generované třídy**. Klikněte na tlačítko se třemi tečkami se uložit název souboru do umístění podle vašeho výběru. Soubor se neukládá do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.

   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda má být připojen implementace třídy do obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.

## <a name="see-also"></a>Viz také

[Přidání třídy z ovládacího prvku ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)<br>
[Klienti automatizace: Použití knihoven typů](../mfc/automation-clients-using-type-libraries.md)