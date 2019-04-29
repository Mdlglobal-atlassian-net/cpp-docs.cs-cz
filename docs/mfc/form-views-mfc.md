---
title: Zobrazení formulářů (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: f93f65e949c18ddb1ad5dba859ba8c4832abac8f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392827"
---
# <a name="form-views-mfc"></a>Zobrazení formulářů (MFC)

Formuláře můžete přidat do jakékoli aplikace Visual C++, který podporuje knihovnu MFC, včetně [aplikace založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md) (jeden jejichž zobrazení třídy je odvozen z `CFormView`). Pokud jste původně nevytvořili aplikace pro potřeby podpory formulářů, bude Visual C++ přidání této podpory za vás při vložení nového formuláře. V aplikaci SDI nebo MDI, která implementuje výchozí [document/view – architektura](../mfc/document-view-architecture.md), když uživatel vybere **nový** příkaz (ve výchozím nastavení, na **souboru** nabídek), Visual C++ vyzve uživatele k vyberte z dostupných formulářů.

Pomocí aplikace SDI, když uživatel vybere **nový** příkaz aktuální instance formuláře nadále běží, ale pokud je vytvořena nová instance aplikace na vybraný formulář. V aplikaci MDI aktuální instance formuláře nadále spouštět, když uživatel klikne **nový** příkazu.

> [!NOTE]
>  Formulář můžete vložit do aplikace založené na dialogu (jeden jehož třídy dialogového okna je založený na `CDialog` a jeden v žádné zobrazení, které je implementované třídy). Ale bez architekturu document/view Visual C++ neimplementuje automaticky **souboru**&#124;**nový** funkce. Je nutné vytvořit způsob, jak si chcete zobrazit další způsoby, například implementací dialogového okna s kartami s použitím různých stránek vlastností uživatele.

Při vložení nového formuláře do aplikace Visual C++ provede následující akce:

- Vytvoří třídu na základě jedné třídy stylu formuláře, které zvolíte (`CFormView`, `CRecordView`, `CDaoRecordView`, nebo `CDialog`).

- Vytvoří prostředek dialogového okna s odpovídající styly (nebo můžete použít existující prostředek dialogu, který ještě nebyl přidružen Class).

   Pokud zvolíte existující prostředek dialogového okna, budete muset nastavit tyto styly pomocí stránky vlastností pro dialogové okno. Styly pro dialogové okno, musí obsahovat:

     **WS_CHILD**=On

     **WS_BORDER**=Off

     **WS_VISIBLE**=Off

     **WS_CAPTION**= vypnuto

Pro aplikace založené na architektuře document/view **nový formulář** příkazu (klikněte pravým tlačítkem v zobrazení tříd) také:

- Vytvoří `CDocument`– na základě třídy

   Namísto toho, aby vytvořili novou třídu, můžete použít všechny existující `CDocument`– na základě třídu ve vašem projektu.

- Vygeneruje šablonu dokumentu (odvozený od `CDocument`) s prostředky řetězce, nabídky a ikony.

   Můžete také vytvořit novou třídu, na kterém chcete založit šabloně.

- Přidá volání `AddDocumentTemplate` ve vaší aplikaci `InitInstance` kódu.

   Visual C++ přidá tento kód pro každý nový formulář vytvoříte, který přidá do seznamu dostupných formulářů formuláře, když uživatel vybere **nový** příkazu. Tento kód obsahuje ID přidružený prostředek formuláře a názvy přidružený dokument, zobrazení a snímků tříd, které společně tvoří nový objekt formuláře.

   Šablony dokumentů slouží jako propojení mezi dokumenty, oken s rámečkem a zobrazení. Pro jednotlivý dokument můžete vytvořit mnoho šablon.

Další informace naleznete v tématu:

- [Vytvoření aplikace založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Vložení formuláře do projektu](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
