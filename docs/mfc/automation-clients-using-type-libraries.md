---
title: "Klienti automatizace: Použití knihoven typů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MkTypLib
dev_langs: C++
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 696765451079301e2a25cc831c34e41802dd33f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="automation-clients-using-type-libraries"></a>Klienti automatizace: Použití knihoven typů
Klienti automatizace musí mít informace o vlastnosti a metody serveru objekty, když jsou klienti k manipulaci s objekty servery. Vlastnosti mají datové typy; metody často návratové hodnoty a přijměte parametry. Klient vyžaduje informace o typech dat všechny tyto staticky vytvořit vazbu na typ serveru.  
  
 Tento typ informací lze známé několika způsoby. Doporučený způsob je vytvoření knihovny typů.  
  
 Informace o [MkTypLib –](http://msdn.microsoft.com/library/windows/desktop/aa366797), najdete v části Windows SDK.  
  
 Visual C++ může číst soubor knihovny typů a vytvořit odesílání třídy odvozené od [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Operace u objektu serveru duplikování a vlastnosti má objekt této třídy. Vaše aplikace volání operace a vlastnosti tohoto objektu, a funkce zděděno z `COleDispatchDriver` směruje těchto volání OLE systém, který pak směruje je do objektu serveru.  
  
 Pokud jste se rozhodli zahrnout automatizace při vytvoření projektu Visual C++ automaticky udržuje tento soubor knihovny typů pro vás. V rámci každé sestavení budou vytvořeny souboru .tlb s MkTypLib –.  
  
### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Pro vytvoření třídy odesílání ze souboru knihovny typů (.tlb)  
  
1.  V zobrazení tříd nebo v Průzkumníku řešení klikněte pravým tlačítkem na projekt a klikněte na tlačítko **přidat** a pak klikněte na **přidat třídu** v místní nabídce.  
  
2.  V **přidat třídu** dialogové okno, vyberte **Visual c + +/ MFC** složku v levém podokně. Vyberte **třídy knihovny MFC z knihovny TypeLib** na ikonu pravém podokně a klikněte na tlačítko **otevřete**.  
  
3.  V **přidat třídu z Průvodce Typelib** dialogu vyberte z knihovny typů **dostupné knihovny typů** rozevíracího seznamu. **Rozhraní** pole zobrazuje rozhraní pro vybraný typ knihovny k dispozici.  
  
    > [!NOTE]
    >  Rozhraní můžete vybrat z více než jeden typ knihovny.  
  
     Vyberte rozhraní, klikněte dvakrát na jejich nebo kliknutím na tlačítko **přidat** tlačítko. Pokud tak učiníte, názvy tříd, odesílání se objeví v **generované třídy** pole. Názvy tříd v můžete upravit `Class` pole.  
  
     **Souboru** pole zobrazuje souboru, ve kterém bude třídu deklarovat. (Tento název souboru také můžete upravovat). Také můžete na tlačítko Procházet a vyberte další soubory, pokud chcete, aby informace hlavičky a implementace napsaný v existující soubory nebo adresáře než adresáři projektu.  
  
    > [!NOTE]
    >  Všechny třídy odesílání pro vybrané rozhraní bude přepnut do zde zadaný soubor. Pokud chcete, aby rozhraní deklarovat v samostatných hlavičky, musíte spustit tohoto průvodce pro každý soubor hlaviček, který chcete vytvořit.  
  
    > [!NOTE]
    >  Některé informace o typu knihovna mohou být uloženy v souborech s. KNIHOVNU DLL. OCX, nebo. OLB přípony souboru.  
  
4.  Klikněte na tlačítko **Dokončit**.  
  
     Průvodce bude zapište kód pro odesílání tříd pomocí zadané třídy a názvy souborů.  
  
## <a name="see-also"></a>Viz také  
 [Klienti automatizace](../mfc/automation-clients.md)

