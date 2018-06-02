---
title: Přidání třídy z Průvodce ovládacím prvkem ActiveX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.axcontrol
dev_langs:
- C++
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ab96943e47287c9b54753c8d3a1edb868804274
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33336814"
---
# <a name="add-class-from-activex-control-wizard"></a>Přidání třídy z průvodce ovládacím prvkem ActiveX
Pomocí tohoto průvodce k přidání třídy knihovny MFC z ovládacího prvku ActiveX k dispozici. Průvodce vytvoří třídu pro každé rozhraní, které přidáte z vybraný ovládací prvek ActiveX.  
  
 **Přidání třídy z**  
 Určuje umístění knihovny typů, ze kterého je vytvořen třídy.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Registru**|Knihovny typů je zaregistrován v systému. Registrovaného typu knihovny jsou uvedeny v **ovládací prvky ActiveX k dispozici**.|  
|**Soubor**|Knihovny typů není nutně zaregistrována v systému, ale je obsažený v souboru. Je nutné zadat umístění souboru v **umístění**.|  
  
 **K dispozici ovládací prvky ActiveX**  
 Určuje ovládací prvky ActiveX, které jsou aktuálně registrované v systému. Vyberte ze seznamu zobrazíte jeho rozhraní ovládacího prvku ActiveX **rozhraní** seznamu. V tématu [MFC – ovládací prvky ActiveX: distribuce ovládacích prvků ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) Další informace o registraci ovládacích prvků ActiveX.  
  
 Pokud kliknete na tlačítko **soubor** pod **přidat třídu z**, toto políčko není možné měnit.  
  
 **Poloha**  
 Určuje umístění ovládacího prvku ActiveX. Pokud kliknete na tlačítko **soubor** pod **přidat třídu z**, můžete zadat umístění souboru, který obsahuje knihovny typů. Chcete-li přejděte do umístění souboru, klikněte na tlačítko se třemi tečkami.  
  
 Pokud kliknete na tlačítko **registru** pod **přidat třídu z**, toto políčko není možné měnit.  
  
 **Rozhraní**  
 Určuje rozhraní v ovládacím prvku ActiveX v aktuálně vybranou **ovládací prvky ActiveX k dispozici** nebo v knihovně typů v zadaném v souboru **umístění**.  
  
|Tlačítko přenosu|Popis|  
|---------------------|-----------------|  
|**>**|Přidá rozhraní vybrané v **rozhraní** seznamu. Tato možnost je k dispozici, pokud není vybrané žádné rozhraní.|  
|**>>**|Přidá všechna rozhraní v ovládacím prvku ActiveX v aktuálně vybranou **ovládací prvky ActiveX k dispozici** nebo v knihovně typů v zadaném v souboru **umístění**.|  
|**<**|Odebere aktuálně vybranou v třídu **generované třídy** seznamu. Není k dispozici, pokud neexistuje žádná třída je v vybrané **generované třídy** seznamu.|  
|**<\<**|Odebere všechny třídy v **generované třídy** seznamu. Pokud není k dispozici **generované třídy** seznam je prázdný.|  
  
 **Vygenerované třídy**  
 Určuje názvy tříd, které mají být vygenerovány z rozhraní přidaných pomocí **>** nebo **>>** tlačítko. Můžete kliknutím na toto políčko, vyberte třídu a potom pomocí nahoru a dolů klíče vyhledejte v seznamu zobrazuje název každé třídy v `Class` a název souboru v **soubor h** pole, které průvodce generuje po kliknutí na tlačítko  **Dokončit**. V tomto poli můžete vybrat jenom jedna třída najednou.  
  
 Třídu můžete odebrat výběrem v tomto seznamu a kliknutím na **<**. Není potřeba vyberte třídu v **generované třídy** pole odebrat všechny třídy; pomocí kliknutím na tlačítko **<<**, odeberete všechny třídy v **generované třídy** pole.  
  
 `Class`  
 Určuje název třídy vybraný v **generované třídy** pole, které průvodce přidá po kliknutí na tlačítko **Dokončit**. Můžete upravit název v `Class` pole.  
  
 **soubor h**  
 Nastaví název hlavičky souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu poskytují v **generované třídy**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby nebo připojit k existující soubor deklaraci třídy. Pokud zvolíte existující soubor, průvodce jej neuloží do vybraného umístění dokud klikněte na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být deklaraci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **souboru**  
 Nastaví název souboru implementace pro nový objekt třídu. Ve výchozím nastavení, tento název je založen na názvu poskytují v **generované třídy**. Klikněte na tlačítko se třemi tečkami uložíte soubor do umístění podle vaší volby. Soubor se neuloží do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být implementaci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
## <a name="see-also"></a>Viz také  
 [Přidání třídy z ovládacího prvku ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)   
 [Klienti automatizace: Použití knihoven typů](../mfc/automation-clients-using-type-libraries.md)