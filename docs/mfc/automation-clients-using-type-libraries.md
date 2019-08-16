---
title: 'Klienti automatizace: Použití knihoven typů'
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
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
ms.openlocfilehash: 480f8fca46b13d445f372311ed837475c71a1e9d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509216"
---
# <a name="automation-clients-using-type-libraries"></a>Klienti automatizace: Použití knihoven typů

Pokud klienti mají manipulovat s objekty serverů, musí mít klienti služby Automation informace o vlastnostech a metodách serverových objektů. Vlastnosti mají datové typy; metody často vracejí hodnoty a přijímají parametry. Klient vyžaduje informace o datových typech všech těchto objektů, aby bylo možné staticky vytvořit vazby na typ objektu serveru.

Tyto informace o typu mohou být známy několika způsoby. Doporučeným způsobem je vytvořit knihovnu typů.

Informace o [MkTypLib](/windows/win32/Midl/differences-between-midl-and-mktyplib)najdete v Windows SDK.

Vizuál C++ může číst soubor knihovny typů a vytvořit třídu Dispatch odvozenou od [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md). Objekt této třídy má vlastnosti a operace, které duplikují objekty objektu serveru. Vaše aplikace volá vlastnosti a operace tohoto objektu a funkce zděděné z `COleDispatchDriver` tras volá do systému OLE, který je následně směruje na objekt serveru.

Vizuál C++ automaticky udržuje tento soubor knihovny typů, pokud se rozhodnete zahrnout automatizaci při vytvoření projektu. V rámci každého sestavení bude soubor. tlb sestaven pomocí MkTypLib.

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>Vytvoření třídy Dispatch ze souboru knihovny typů (. tlb)

1. V Zobrazení tříd nebo Průzkumník řešení klikněte pravým tlačítkem myši na projekt a klikněte na **Přidat** a potom v místní nabídce klikněte na **Přidat třídu** .

1. V dialogovém okně **Přidat třídu** vyberte v levém podokně **složku C++Visual/MFC** . V pravém podokně vyberte ikonu **knihovny MFC z tabulky TypeLib** a klikněte na **otevřít**.

1. V dialogovém okně **Průvodce přidáním třídy z TypeLib** vyberte knihovnu typů z rozevíracího seznamu **Dostupné knihovny typů** . Pole **rozhraní** zobrazuje rozhraní dostupná pro vybranou knihovnu typů.

    > [!NOTE]
    >  Můžete vybrat rozhraní z více než jedné knihovny typů.

   Pokud chcete vybrat rozhraní, poklikejte na ně nebo klikněte na tlačítko **Přidat** . V takovém případě se názvy pro třídy odeslání zobrazí v poli vygenerované **třídy** . V `Class` poli můžete upravit názvy tříd.

   V poli **soubor** se zobrazí soubor, ve kterém bude třída deklarována. (můžete také upravit tento název souboru). Můžete také použít tlačítko Procházet a vybrat jiné soubory, pokud upřednostňujete, aby byly informace hlavičky a implementace napsány v existujících souborech nebo v jiném adresáři, než v adresáři projektu.

    > [!NOTE]
    >  Všechny třídy odeslání pro vybraná rozhraní budou vloženy do zadaného souboru. Pokud chcete, aby byla rozhraní deklarována v samostatných hlavičkách, je nutné spustit tohoto průvodce pro každý hlavičkový soubor, který chcete vytvořit.

    > [!NOTE]
    >  Některé informace o knihovně typů mohou být uloženy v souborech s. KNIHOVNA DLL,. OCX nebo. Přípony souborů OLB

1. Klikněte na tlačítko **Dokončit**.

   Průvodce pak zapíše kód pro vaše třídy odeslání pomocí zadané třídy a názvů souborů.

## <a name="see-also"></a>Viz také:

[Klienti automatizace](../mfc/automation-clients.md)
