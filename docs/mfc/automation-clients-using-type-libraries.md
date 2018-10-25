---
title: 'Klienti automatizace: Použití knihoven typů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MkTypLib
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 001dfb29a5ac0f6d93b0715bd2b86ccd60e91259
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054602"
---
# <a name="automation-clients-using-type-libraries"></a>Klienti automatizace: Použití knihoven typů

Klienti automatizace musí mít informace o vlastnostech a metodách objekty serveru, pokud jsou klienti k manipulaci s objekty na servery. Vlastnosti mají datové typy; metody často návratové hodnoty a přijímají parametry. Klient vyžaduje informace o datových typech všechny tyto staticky vázat na typ objektu serveru.

Informace o tomto typu lze provést několika způsoby známé. Doporučený postup je vytvořit knihovnu typů.

Informace o [s MkTypLib](/windows/desktop/Midl/differences-between-midl-and-mktyplib), naleznete v sadě Windows SDK.

Visual C++ může číst soubor knihovny typů a vytvořit odeslání třídy odvozené od [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Vlastnosti a operace u objektu serveru duplikování má objekt této třídy. Vaše aplikace volá vlastností a operací objektu nebo funkce zděděním od `COleDispatchDriver` trasy těchto volání OLE systému, který pak směruje je do objektu serveru.

Pokud jste se rozhodli zahrnují Automation při vytvoření projektu jazyka Visual C++ automaticky udržuje tento soubor knihovny typů za vás. Jako součást každé sestavení bude se s MkTypLib vytvořen souboru .tlb.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Chcete-li vytvořit třídu odeslání ze souboru knihovny typů (.tlb)

1. V zobrazení tříd nebo v Průzkumníku řešení klikněte pravým tlačítkem na projekt a klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat třídu** v místní nabídce.

1. V **přidat třídu** dialogové okno, vyberte **Visual vyhodnocování +/ MFC** složky v levém podokně. Vyberte **třídy knihovny MFC z TypeLib** ikonu v pravém podokně a kliknutím **otevřít**.

1. V **přidání třídy z Průvodce knihovnou typů** dialogového okna, vyberte z knihovny typů **dostupné knihovny typů** rozevíracího seznamu. **Rozhraní** pole zobrazí rozhraní, které jsou k dispozici pro vybrané knihovny typů.

    > [!NOTE]
    >  Rozhraní můžete vybrat z víc než jedné knihovny typů.

   Vyberte rozhraní, dvakrát klikněte na ně nebo klikněte na tlačítko **přidat** tlačítko. Pokud tak učiníte, názvy tříd, odeslání se zobrazí v **generované třídy** pole. Můžete upravit názvy tříd v `Class` pole.

   **Souboru** pole zobrazí soubor, ve kterém se deklarovat třídu. (můžete upravit tento soubor název). Pokud chcete mít záhlaví tak implementační informace, které jsou napsané v existující soubory nebo na jiný adresář než adresáře projektu, můžete použít také na tlačítko Procházet a vyberte další soubory.

    > [!NOTE]
    >  Všechny třídy odeslání pro vybrané rozhraní zařadí do zde zadaného souboru. Pokud chcete rozhraní být deklarován v samostatných záhlaví, musíte spustit tohoto průvodce pro každý soubor hlaviček, které chcete vytvořit.

    > [!NOTE]
    >  Některé informace knihovny typů mohou být uloženy v souborech s. KNIHOVNY DLL. OCX, nebo. OLB přípon souborů.

1. Klikněte na tlačítko **Dokončit**.

   Průvodce potom psát kód pro odesílání třídy pomocí zadané třídy a názvy souborů.

## <a name="see-also"></a>Viz také

[Klienti automatizace](../mfc/automation-clients.md)

