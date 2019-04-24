---
title: OLE – pozadí
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: 2501373c2ff5904343a6522e4fb18663f5de3843
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186586"
---
# <a name="ole-background"></a>OLE – pozadí

OLE je mechanismus, který umožňuje uživatelům vytvářet a upravovat dokumenty, které obsahují položky nebo "objekty" vytvořil několik aplikací.

> [!NOTE]
>  OLE byl původně zkratka pro propojování a vkládání objektů. Ale to se teď nazývá OLE. Části OLE, které nesouvisí s propojování a vkládání jsou teď součástí technologie Active.

Dokumenty OLE, volá se v minulosti složených dokumentů, bez problémů integrovat různé typy dat nebo komponenty. Zvukové soubory, tabulky a rastrových obrázků jsou typické příklady komponent v dokumenty OLE. Podpora OLE ve vaší aplikaci umožňuje uživatelům používat OLE – dokumenty bez starostí o přepínání mezi různými aplikacemi; OLE neodpovídá přepínání za vás.

Použití aplikace typu kontejner pro vytvoření složené dokumenty a serverové aplikace nebo komponenty aplikace pro vytváření položek v rámci dokumentu kontejneru. Kontejner a server může být jakékoli aplikace, kterou píšete.

OLE – zahrnuje mnoho různých koncepty všechny pracovní směrem k cíli bezproblémové interakce mezi aplikacemi. Tyto oblasti patří:

- Propojování a vkládání

   Propojování a vkládání jsou dvě metody pro ukládání položek vytvořený v dokumentu OLE, které byly vytvořeny v jiné aplikaci. Obecné informace o rozdílech mezi těmito dvěma, najdete v článku [OLE pozadí: Propojování a vkládání](../mfc/ole-background-linking-and-embedding.md). Podrobnější informace najdete v článcích [kontejnery](../mfc/containers.md) a [servery](../mfc/servers.md).

- Aktivace na místě (vizuální úpravy)

   Aktivaci vložené položky v rámci dokumentu kontejneru se nazývá aktivace na místě nebo úpravy s náhledem. Aplikace typu kontejner rozhraní se změní na začlenit funkce komponenty aplikace, která vytvoří vloženou položku. Propojené položky jsou nikdy neaktivoval na místě, protože skutečná data pro položku je obsažen v samostatném souboru mimo kontext aplikace obsahující odkaz. Další informace o aktivace na místě, najdete v článku [aktivace](../mfc/activation-cpp.md).

   > [!NOTE]
   > Propojování a vkládání a aktivace na místě si hlavní funkce úpravy s náhledem OLE.

- Automatizace služby Automation umožňuje jednu aplikaci Centrum umožňující prosazovat jiná aplikace. Řízení aplikací se označuje jako klient automatizace a aplikace se řízené se označuje jako automatizační server nebo součást automatizace. Další informace o automatizaci, najdete v článcích [klientům automatizace](../mfc/automation-clients.md) a [automatizační servery](../mfc/automation-servers.md).

   > [!NOTE]
   > Služba Automation funguje v kontextu technologie OLE a aktivní. Můžete automatizovat objekty založené na modelu COM.

- Složené soubory

   Složené soubory poskytovat standardní formát souboru, který zjednodušuje ukládání strukturovaných složených dokumentů pro aplikací OLE. V rámci souboru složené úložných mají mnoho funkcí adresáře a datové proudy mají mnoho funkcí souborů. Tato technologie se také nazývá strukturované úložiště. Další informace o složené soubory, najdete v článku [kontejnerů: Složené soubory](../mfc/containers-compound-files.md).

- Jednotný přenos dat

   Jednotné přenos dat (UDT) je sada rozhraní, která se mají odesílat a přijímat standardním způsobem, bez ohledu na skutečnou metoda zvolili k přenosu dat data. UDT formuláře, které základ pro data se přenáší pomocí přetažení. UDT nyní slouží jako základ pro stávající přenosy dat Windows, jako je schránka a dynamickou výměnu dat (DDE). Další informace o UDT, najdete v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md).

- Přetažení

   Přetažení je snadné použití, manipulaci se soubory přímo způsob přenosu dat mezi aplikacemi, mezi okny v rámci aplikace, nebo dokonce i v rámci jednoho okna v aplikaci. Přenos dat je vybraná a přetáhnout do požadovaného cíle. Přetažení je založená na přenos dat jednotné. Další informace o přetahování, najdete v článku [přetažení](../mfc/drag-and-drop-ole.md).

- Component Object Model

   Modelu COM (Component Object) poskytuje infrastrukturu použít při komunikaci objekty OLE. Třídy MFC OLE COM zjednodušit programátorovi. COM je součástí technologie Active, protože objekty modelu COM tvoří základ technologie OLE a aktivní. Další informace o modelu COM, najdete v článku [aktivní šablony knihovny (ATL)](../atl/active-template-library-atl-concepts.md) témata.

Některé další důležitá témata OLE jsou popsané v následujících článcích:

- [OLE – pozadí: Propojování a vkládání](../mfc/ole-background-linking-and-embedding.md)

- [OLE – pozadí: Kontejnery a servery](../mfc/ole-background-containers-and-servers.md)

- [OLE – pozadí: Strategie implementace](../mfc/ole-background-implementation-strategies.md)

- [OLE – pozadí: Implementace v prostředí MFC](../mfc/ole-background-mfc-implementation.md)

Obecné informace OLE nebyl nalezen ve výše uvedených článcích vyhledejte OLE na webu MSDN.

## <a name="see-also"></a>Viz také:

[OLE](../mfc/ole-in-mfc.md)
