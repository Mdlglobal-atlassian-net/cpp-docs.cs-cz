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
ms.openlocfilehash: 5e8912c9013175fe254b2f4a4a968a67fd071f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365302"
---
# <a name="form-views-mfc"></a>Zobrazení formulářů (MFC)

Formuláře můžete přidat do libovolné aplikace visual c++, která podporuje knihovny knihovny Knihovny MFC, včetně [aplikace založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md) (z aplikace, jejíž třída zobrazení je odvozena z). `CFormView` Pokud jste původně nevytvořili aplikaci pro podporu formulářů, visual c++ přidá tuto podporu při vložení nového formuláře. V aplikaci SDI nebo MDI, která implementuje výchozí [architekturu dokumentu nebo zobrazení](../mfc/document-view-architecture.md), když uživatel zvolí příkaz **Nový** (ve výchozím nastavení v nabídce **Soubor),** visual c++ vyzve uživatele k výběru z dostupných formulářů.

S aplikací SDI, když uživatel zvolí příkaz **Nový,** aktuální instance formuláře pokračuje v běhu, ale pokud není nalezena, vytvoří se nová instance aplikace s vybraným formulářem. V aplikaci MDI aktuální instance formuláře nadále běžet, když uživatel zvolí **nový** příkaz.

> [!NOTE]
> Formulář můžete vložit do aplikace založené na dialogu (aplikace, `CDialog` na jejíž třídě dialogů je založena, a do aplikace, ve které není implementována žádná třída zobrazení). Však bez architektury dokumentu/zobrazení Visual C++ neimplementuje automaticky **soubor**&#124;**nové** funkce. Je nutné vytvořit způsob, jakým může uživatel zobrazit další formuláře, například implementací dialogového okna s kartami s různými stránkami vlastností.

Když do aplikace vložíte nový formulář, visual c++ udělá následující:

- Vytvoří třídu založenou na jedné z tříd`CFormView`ve `CRecordView` `CDaoRecordView`stylu `CDialog`formuláře, které zvolíte ( , , , nebo ).

- Vytvoří prostředek dialogu s příslušnými styly (nebo můžete použít existující prostředek dialogového okna, který ještě nebyl přidružen ke třídě).

   Pokud zvolíte existující prostředek dialogu, bude pravděpodobně nutné nastavit tyto styly pomocí stránky Vlastnosti dialogového okna. Styly pro dialogové okno musí obsahovat:

     **WS_CHILD**=Zapnuto

     **WS_BORDER**=Vypnuto

     **WS_VISIBLE**=Vypnuto

     **WS_CAPTION**=Vypnuto

U aplikací založených na architektuře dokumentu/zobrazení také příkaz **Nový formulář** (kliknutí pravým tlačítkem myši v zobrazení třídy):

- Vytvoří `CDocument`třídu založenou na

   Místo vytvoření nové třídy můžete v `CDocument`projektu použít libovolnou existující třídu založenou na.

- Generuje šablonu dokumentu (odvozenou z) `CDocument`s řetězci, nabídkami a prostředky ikon.

   Můžete také vytvořit novou třídu, na které založit šablonu.

- Přidá volání `AddDocumentTemplate` v `InitInstance` kódu aplikace.

   Visual C++ přidá tento kód pro každý nový formulář, který vytvoříte, který přidá formulář do seznamu dostupných formulářů, když uživatel zvolí příkaz **Nový.** Tento kód obsahuje přidružené ID prostředku formuláře a názvy přidružených tříd dokumentu, zobrazení a rámce, které společně tvoří nový objekt formuláře.

   Šablony dokumentů slouží jako spojení mezi dokumenty, okny rámců a zobrazeními. Pro jeden dokument můžete vytvořit mnoho šablon.

Další informace naleznete v tématu:

- [Vytvoření aplikace založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Vložení formuláře do projektu](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
