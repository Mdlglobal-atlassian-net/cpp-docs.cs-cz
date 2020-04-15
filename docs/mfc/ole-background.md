---
title: OLE – pozadí
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: f7d65f48c1af678f6626ba7d315ceb735d3e960a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364520"
---
# <a name="ole-background"></a>OLE – pozadí

OLE je mechanismus, který umožňuje uživatelům vytvářet a upravovat dokumenty obsahující položky nebo "objekty" vytvořené více aplikacemi.

> [!NOTE]
> OLE byla původně zkratka pro propojení a vkládání objektů. Však nyní označuje jako OLE. Části OLE, které nesouvisí s propojením a vkládáním, jsou nyní součástí technologie Active.

Dokumenty OLE, historicky nazývané složené dokumenty, bezproblémově integrují různé typy dat nebo komponent. Zvukové klipy, tabulky a bitmapy jsou typickými příklady součástí nalezených v dokumentech OLE. Podpora OLE v aplikaci umožňuje uživatelům používat dokumenty OLE bez obav o přepínání mezi různými aplikacemi; OLE provádí přepínání za vás.

Aplikace kontejneru slouží k vytvoření složených dokumentů a serverové aplikace nebo součásti aplikace k vytvoření položek v dokumentu kontejneru. Každá aplikace, kterou napíšete, může být kontejner, server nebo obojí.

OLE zahrnuje mnoho různých konceptů, které všechny pracují směrem k cíli bezproblémové interakce mezi aplikacemi. Mezi tyto oblasti patří:

- Propojování a vkládání

   Propojení a vkládání jsou dvě metody pro ukládání položek vytvořených v dokumentu OLE, které byly vytvořeny v jiné aplikaci. Obecné informace o rozdílech mezi těmito dvěma naleznete v článku [OLE Background: Linking and Embedding](../mfc/ole-background-linking-and-embedding.md). Podrobnější informace naleznete v článcích [Kontejnery](../mfc/containers.md) a [servery](../mfc/servers.md).

- Aktivace na místě (vizuální úpravy)

   Aktivace vložené položky v kontextu dokumentu kontejneru se nazývá aktivace na místě nebo vizuální úpravy. Rozhraní aplikace kontejneru se změní tak, aby zahrnovalo funkce aplikace komponenty, která vytvořila vloženou položku. Propojené položky nejsou nikdy aktivovány na místě, protože skutečná data pro položku jsou obsažena v samostatném souboru mimo kontext aplikace obsahující odkaz. Další informace o aktivaci na místě naleznete v článku [Aktivace](../mfc/activation-cpp.md).

   > [!NOTE]
   > Propojení a vkládání a aktivace na místě poskytují hlavní funkce vizuální úpravy OLE.

- Automatizace automatizace umožňuje jedné aplikaci řídit jinou aplikaci. Aplikace řízení se označuje jako klient automatizace a řízená aplikace se označuje jako automatizační server nebo součást automatizace. Další informace o automatizaci naleznete v článcích [Automation Clients](../mfc/automation-clients.md) and [Automation Servers](../mfc/automation-servers.md).

   > [!NOTE]
   > Automatizace funguje v kontextu OLE i active technologie. Můžete automatizovat libovolný objekt na základě com.

- Složené soubory

   Složené soubory poskytují standardní formát souborů, který zjednodušuje strukturované ukládání složených dokumentů pro aplikace OLE. V rámci složeného souboru mají úložiště mnoho funkcí adresářů a datové proudy mají mnoho funkcí souborů. Tato technologie se také nazývá strukturované úložiště. Další informace o složených souborech naleznete v článku [Kontejnery: Složené soubory](../mfc/containers-compound-files.md).

- Jednotný přenos dat

   Jednotný přenos dat (UDT) je sada rozhraní, která umožňují odesílat a přijímat data standardním způsobem, bez ohledu na skutečnou metodu zvolenou pro přenos dat. UDT tvoří základ pro přenos dat přetažením. UDT nyní slouží jako základ pro existující přenos dat systému Windows, jako je například schránka a dynamická výměna dat (DDE). Další informace o UDT naleznete v článku [Datové objekty a zdroje dat (OLE).](../mfc/data-objects-and-data-sources-ole.md)

- Přetažení

   Drag and drop je snadno použitelná technika přímé manipulace pro přenos dat mezi aplikacemi, mezi okny v rámci aplikace nebo dokonce v rámci jednoho okna v aplikaci. Data, která mají být přenesena, jsou vybrána a přetažena na požadovaný cíl. Přetažení je založeno na jednotném přenosu dat. Další informace o přetažení naleznete v článku [Přetažení](../mfc/drag-and-drop-ole.md).

- Objektový model komponenty

   Model COM (COM) poskytuje infrastrukturu používanou při vzájemné komunikaci objektů OLE. Třídy OLE knihovny MFC zjednodušují com pro programátora. COM je součástí aktivní technologie, protože objekty COM jsou základem technologie OLE i Active. Další informace o com naleznete [v tématech knihovny knihovny šablon (ATL).](../atl/active-template-library-atl-concepts.md)

Některá z nejdůležitějších témat OLE jsou popsána v následujících článcích:

- [OLE – pozadí: Propojování a vkládání](../mfc/ole-background-linking-and-embedding.md)

- [OLE – pozadí: Kontejnery a servery](../mfc/ole-background-containers-and-servers.md)

- [OLE – pozadí: Strategie implementace](../mfc/ole-background-implementation-strategies.md)

- [OLE – pozadí: Implementace MFC](../mfc/ole-background-mfc-implementation.md)

Obecné informace OLE, které nebyly nalezeny ve výše uvedených článcích, vyhledejte ole v MSDN.

## <a name="see-also"></a>Viz také

[OLE](../mfc/ole-in-mfc.md)
