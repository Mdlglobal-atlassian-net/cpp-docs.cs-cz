---
title: "Přidání třídy z Průvodce Typelib | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4aad89b6f3227cac59b6429cc67975db3dad424
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="add-class-from-typelib-wizard"></a>Přidání třídy z průvodce knihovnou typů
Pomocí tohoto průvodce můžete přidat třídy knihovny MFC z knihovny k dispozici typu. Průvodce vytvoří třídu pro každé rozhraní, které přidáte z knihovny vybraného typu.  
  
 **Přidání třídy z**  
 Určuje umístění knihovny typů, ze kterého je vytvořen třídy.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Registru**|Knihovny typů je zaregistrován v systému. Registrovaného typu knihovny jsou uvedeny v **dostupné knihovny typů**.|  
|**Soubor**|Knihovny typů není nutně zaregistrována v systému, ale je obsažený v souboru. Je nutné zadat umístění souboru v **umístění**.|  
  
 **Dostupné knihovny typů**  
 Uvádí knihovny typů, které jsou aktuálně registrované v systému. Vyberte knihovnu typu z tohoto seznamu zobrazíte jeho rozhraní **rozhraní** seznamu.  
  
 Najdete v části "Uvnitř Distributed COM: typ knihovny a jazyk integrace" v knihovně MSDN Další informace o registraci knihovny typů.  
  
 **Umístění**  
 Určuje umístění knihovny typů. Pokud kliknete na tlačítko **soubor** pod **přidat třídu z**, můžete zadat umístění souboru, který obsahuje knihovny typů. Chcete-li přejděte do umístění souboru, klikněte na tlačítko se třemi tečkami.  
  
 **Rozhraní**  
 Seznam rozhraní v aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu.  
  
|Tlačítko přenosu|Popis|  
|---------------------|-----------------|  
|**>**|Přidá rozhraní vybrané v **rozhraní** seznamu. Nedostupné, pokud není vybrané žádné rozhraní.|  
|**>>**|Přidá všechna rozhraní v aktuálně vybrané v knihovně typů **dostupné knihovny typů** seznamu.|  
|**<**|Odebere aktuálně vybranou v třídu **generované třídy** seznamu. Nedostupné, pokud neexistuje žádná třída v aktuálně vybranou **generované třídy** seznamu.|  
|**<\<**|Odebere všechny třídy v **generované třídy** seznamu. Pokud neaktivní **generované třídy** seznam je prázdný.|  
  
 **Vygenerované třídy**  
 Určuje názvy tříd, které mají být vygenerovány z rozhraní přidaných pomocí  **>**  nebo  **>>**  tlačítko. Můžete kliknutím na toto políčko, vyberte třídu a potom pomocí nahoru a dolů klíče vyhledejte v seznamu zobrazuje název každé třídy v `Class` a název souboru v **soubor** pole, které průvodce generuje po kliknutí na tlačítko  **Dokončit**. V tomto poli můžete vybrat jenom jedna třída najednou.  
  
 Třídu můžete odebrat výběrem v tomto seznamu a kliknutím na  **<** . Není nutné k výběru třídy v poli generované třídy odebrat všechny třídy; Kliknutím na  **<<** , odeberte všechny třídy v **generované třídy** pole.  
  
 `Class`  
 Určuje název třídy vybraný v **generované třídy** pole, které průvodce přidá po kliknutí na tlačítko **Dokončit**. Můžete upravit název v `Class` pole.  
  
 **Soubor**  
 Nastaví název hlavičky souboru pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu poskytují v **generované třídy**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby nebo připojit k existující soubor deklaraci třídy. Pokud zvolíte existující soubor, průvodce jej neuloží do vybraného umístění dokud klikněte na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být deklaraci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
## <a name="see-also"></a>Viz také  
 [Třída knihovny MFC z knihovny typů](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Klienti automatizace: Použití knihoven typů](../../mfc/automation-clients-using-type-libraries.md)

