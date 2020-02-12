---
title: 'Kontejnery: Implementace kontejneru'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: ed95324b8df978a6ab2f7582c0ddf626a45e7fe1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127917"
---
# <a name="containers-implementing-a-container"></a>Kontejnery: Implementace kontejneru

Tento článek shrnuje postup pro implementaci kontejneru a odkazuje na další články, které poskytují podrobnější vysvětlení implementace kontejnerů. Také obsahuje seznam některých volitelných funkcí OLE, které můžete chtít implementovat, a článků, které tyto funkce popisují.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Příprava vaší odvozené třídy CWinApp

1. Inicializujte knihovny OLE voláním `AfxOleInit` ve členské funkci `InitInstance`.

1. Zavolejte `CDocTemplate::SetContainerInfo` v `InitInstance` k přiřazení prostředků nabídky a akcelerátoru, které se použijí, když se vložená položka aktivuje místně. Další informace o tomto tématu najdete v tématu [Aktivace](../mfc/activation-cpp.md).

Tyto funkce jsou k dispozici automaticky při použití Průvodce aplikací knihovny MFC k vytvoření aplikace typu kontejner. Viz [vytvoření programu MFC exe](../mfc/reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Příprava třídy zobrazení

1. Můžete sledovat vybrané položky tím, že zachováte ukazatel nebo seznam ukazatelů, Pokud podporujete vícenásobný výběr, na vybrané položky. Vaše funkce `OnDraw` musí nakreslit všechny položky OLE.

1. Přepište `IsSelected` a ověřte, zda je položka předaná do ní aktuálně vybrána.

1. Implementací obslužné rutiny zprávy `OnInsertObject` pro zobrazení dialogového okna **Vložit objekt** .

1. Implementací obslužné rutiny zprávy `OnSetFocus` můžete přenést fokus ze zobrazení na místo na místní aktivní vložené položky OLE.

1. Implementujte obslužnou rutinu `OnSize` zprávy pro informování vložené položky OLE, kterou potřebuje změnit její obdélník, aby odrážela změnu velikosti nadřazeného zobrazení.

Vzhledem k tomu, že implementace těchto funkcí se výrazně liší od jedné aplikace po další, Průvodce aplikací poskytuje jenom základní implementaci. Bude pravděpodobně nutné přizpůsobit tyto funkce, aby aplikace správně fungovala. Příklad najdete v ukázce [kontejneru](../overview/visual-cpp-samples.md) .

#### <a name="to-handle-embedded-and-linked-items"></a>Zpracování vložených a propojených položek

1. Odvodit třídu z [COleClientItem](../mfc/reference/coleclientitem-class.md). Objekty této třídy reprezentují položky, které byly vloženy do nebo připojeny k vašemu dokumentu OLE.

1. Přepsat `OnChange`, `OnChangeItemPosition`a `OnGetItemPosition`. Tyto funkce zpracovávají velikost, umístění a úpravy vložených a propojených položek.

Průvodce aplikací bude třídu odvodit za vás, ale pravděpodobně bude nutné přepsat `OnChange` a další funkce uvedené v tomto postupu v kroku 2 v předchozím postupu. Kostru implementací je nutné přizpůsobit pro většinu aplikací, protože tyto funkce jsou implementovány jinak než jedna z aplikací do další. Příklady naleznete v tématu MFC Samples [DRAWCLI](../overview/visual-cpp-samples.md) a [Container](../overview/visual-cpp-samples.md).

Je nutné přidat počet položek do struktury nabídky aplikace kontejneru, aby bylo možné podporovat OLE. Další informace o těchto tématech naleznete v tématu [nabídky a prostředky: Přidání kontejneru](../mfc/menus-and-resources-container-additions.md).

V aplikaci typu kontejner možná budete chtít podporovat i některé z následujících funkcí:

- Místní aktivace při úpravě vložené položky

   Další informace najdete v tématu [Aktivace](../mfc/activation-cpp.md).

- Vytvoření položek OLE přetažením z serverové aplikace.

   Další informace najdete v tématu [přetahování OLE](../mfc/drag-and-drop-ole.md).

- Odkazy na vložené objekty nebo kombinované aplikace kontejneru/serveru.

   Další informace najdete v tématu [kontejnery: pokročilé funkce](../mfc/containers-advanced-features.md).

## <a name="see-also"></a>Viz také

[Kontejnery](../mfc/containers.md)<br/>
[Kontejnery: Klientské položky](../mfc/containers-client-items.md)
