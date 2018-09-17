---
title: Přidání třídy z Průvodce knihovnou typů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bba9025e8a7529a2809c18eef8bd61ce7f620c0e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724994"
---
# <a name="add-class-from-typelib-wizard"></a>Přidání třídy z průvodce knihovnou typů
Tohoto průvodce použijte k přidání třídy knihovny MFC z knihovny typů k dispozici. Průvodce vytvoří třídu pro každé rozhraní, kterou přidáte z vybrané knihovny typů.  
  
- **Přidat třídu z:**

   Určuje umístění knihovny typů, ze kterého se vytvoří třídu.  
  
   |Možnost|Popis|  
   |------------|-----------------|  
   |**Registru**|Knihovna typů je registrován v systému. Zaregistrované knihovny typů jsou uvedeny v **dostupné knihovny typů**.|  
   |**Soubor**|Knihovna typů není nutně registrován v systému, ale je obsažena v souboru. Je nutné zadat umístění souborů v **umístění**.|  
  
- **Dostupné knihovny typů**

   Obsahuje knihovny typů, které jsou aktuálně registrované v systému. Vyberte knihovnu typů z tohoto seznamu zobrazíte jeho rozhraní **rozhraní** seznamu.  
  
   Viz "Uvnitř Distributed COM: typ a jazyk integrace knihoven" v knihovně MSDN pro další informace o registraci knihovny typů.  
  
- **Poloha**

   Určuje umístění knihovny typů. Vyberete-li **souboru** pod **přidat třídu z**, můžete uvést umístění souboru, který obsahuje knihovnu typů. Přejděte do umístění souboru, klikněte na tlačítko se třemi tečkami.  
  
- **Rozhraní**

   Seznam rozhraní v aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu.  
  
   |Tlačítka převodu|Popis|  
   |---------------------|-----------------|  
   |**>**|Přidá rozhraní vybrané v **rozhraní** seznamu. Neaktivní, pokud není vybrané žádné rozhraní.|  
   |**>>**|Přidá všechna rozhraní v aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu.|  
   |**\<**|Odebere aktuálně vybranou v třídu **generované třídy** seznamu. Neaktivní, pokud žádná třída je aktuálně vybrána v **generované třídy** seznamu.|  
   |**\<\<**|Odebere všechny třídy v **generované třídy** seznamu. Neaktivní if **generované třídy** seznam je prázdný.|  
  
- **Generované třídy**

   Určuje názvy tříd, které mají být vygenerovány z rozhraní přidaných pomocí **>** nebo **>>** tlačítko. Můžete kliknout na toto políčko, aby vyberte třídu a potom použít nahoru nebo dolů kláves procházejte seznam, název každé třídy v zobrazení **třídy** a název souboru v **soubor** pole, Průvodce generuje při můžete Klikněte na tlačítko **Dokončit**. V tomto poli můžete vybrat pouze jednu třídu najednou.  
  
   Třídu můžete odebrat tak, že ji vyberete v tomto seznamu a kliknete na **<**. Není potřeba vybrat třídu do vygenerované třídy pole odebrat všechny třídy; Kliknutím na **<<**, odeberte všechny třídy v **generované třídy** pole.  
  
- **Třída**

   Určuje název třídy vybraný v **generované třídy** pole, které průvodce přidá po kliknutí na **Dokončit**. Můžete upravit název v **třídy** pole.  
  
- **Soubor**

   Nastaví název souboru hlaviček pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu je zadat v **generované třídy**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud zvolíte existující soubor, Průvodce neuloží se do vybraného umístění dokud kliknutím **Dokončit** v průvodci.  
  
   Průvodce nepřepisuje soubor. Pokud jste vybrali název existujícího souboru, po kliknutí na **Dokončit**, Průvodce vás vyzve k označení, zda by měla být k obsah souboru připojen deklaraci třídy. Klikněte na tlačítko **Ano** pro připojení k souboru, klikněte na tlačítko **ne** pro návrat do průvodce a zadejte jiný název souboru.  
  
## <a name="see-also"></a>Viz také  
 [Třída knihovny MFC z knihovny typů](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Klienti automatizace: Použití knihoven typů](../../mfc/automation-clients-using-type-libraries.md)

