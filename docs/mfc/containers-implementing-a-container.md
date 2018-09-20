---
title: 'Kontejnery: Implementace kontejneru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46fa8b115dd01a9ee11442a0701cd719cc6d389e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394358"
---
# <a name="containers-implementing-a-container"></a>Kontejnery: Implementace kontejneru

Tento článek shrnuje postup implementace kontejneru a odkazuje na další články, které poskytují podrobnější vysvětlení o implementaci kontejnery. Obsahuje také seznam některých volitelných funkcí OLE, které můžete implementovat a články popisující, tyto funkce.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Příprava vašich CWinApp odvozených tříd

1. Inicializace knihoven OLE voláním `AfxOleInit` v `InitInstance` členskou funkci.

1. Volání `CDocTemplate::SetContainerInfo` v `InitInstance` přiřazení v nabídce a akcelerátor prostředky používané při vloženou položku je zrovna místně aktivuje. Další informace o tomto tématu najdete v tématu [aktivace](../mfc/activation-cpp.md).

Tyto funkce jsou k dispozici pro vás automaticky při použití Průvodce aplikací knihovny MFC k vytvoření aplikace typu kontejner. Zobrazit [vytvoření aplikace MFC EXE](../mfc/reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Příprava vaší třídy zobrazení

1. Mějte přehled o vybrané položky pomocí ukazatele nebo seznamu ukazatelů, pokud podporujete vícenásobný výběr pro vybrané položky. Vaše `OnDraw` funkce musí kreslení všech položek OLE.

1. Přepsat `IsSelected` ke kontrole, jestli je aktuálně vybrána položka předaná.

1. Implementace `OnInsertObject` obslužná rutina zprávy pro zobrazení **vložit objekt** dialogové okno.

1. Implementace `OnSetFocus` zpráva obslužná rutina se má převést fokus z zobrazení do místní active OLE vložené položky.

1. Implementace `OnSize` obslužné rutiny zpráv informovat OLE vložené položky, že je nutné změnit jeho obdélník tak, aby odrážely změny velikosti jeho nadřazeného zobrazení.

Protože implementaci těchto funkcí se výrazně liší od jedné aplikace na další, Průvodce aplikací poskytuje základní implementaci. Budete pravděpodobně muset upravit tyto funkce pro uvedení aplikace fungovat správně. Příkladem, najdete v článku [KONTEJNERU](../visual-cpp-samples.md) vzorku.

#### <a name="to-handle-embedded-and-linked-items"></a>Pro zpracování vložené a propojené položky

1. Odvodit třídu z [COleClientItem](../mfc/reference/coleclientitem-class.md). Objekty této třídy představují položky, které byly součástí nebo propojené s dokumentu OLE.

1. Přepsat `OnChange`, `OnChangeItemPosition`, a `OnGetItemPosition`. Tyto funkce zpracování pro změnu velikosti, umístění a úpravy vložené a propojené položky.

Průvodce aplikace odvodí třídy za vás, ale bude pravděpodobně nutné přepsat `OnChange` a další funkce uvedené s ním v kroku 2 v předchozím postupu. Kostru implementace muset lze přizpůsobit pro většinu aplikací, protože tyto funkce jsou implementované jinak z jedné aplikace na další. Příklady, najdete v ukázkách MFC [DRAWCLI](../visual-cpp-samples.md) a [KONTEJNERU](../visual-cpp-samples.md).

Počet položek, které je třeba přidat do nabídky struktury aplikace typu kontejner pro podporu technologie OLE. Další informace naleznete v tématu [nabídky a prostředky: kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md).

Můžete také podporovat některé z následujících funkcí v kontejneru aplikace:

- Aktivace na místě při úpravách vloženou položku.

     Další informace najdete v tématu [aktivace](../mfc/activation-cpp.md).

- Vytvoření OLE položky přetahováním výběr ze serverové aplikace.

     Další informace najdete v tématu [oblast pro přetažení přetažení (OLE)](../mfc/drag-and-drop-ole.md).

- Obsahuje odkazy na vložené objekty nebo kombinaci typu server/kontejner aplikace.

     Další informace najdete v tématu [kontejnery: pokročilé funkce](../mfc/containers-advanced-features.md).

## <a name="see-also"></a>Viz také

[Kontejnery](../mfc/containers.md)<br/>
[Kontejnery: Klientské položky](../mfc/containers-client-items.md)

