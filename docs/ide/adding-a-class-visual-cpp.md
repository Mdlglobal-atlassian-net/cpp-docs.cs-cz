---
title: Přidání třídy (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.adding
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2ef8ae3e7620efb74099287dcda29210545d2e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420540"
---
# <a name="adding-a-class-visual-c"></a>Přidání třídy (Visual C++)

Chcete-li přidat třídu v projektu v jazyce Visual C++ v **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **třídy**. Tím se otevře [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md) dialogové okno.

Při přidání třídy, musíte zadat název, který se liší od třídy, které již existují v MFC ani ATL. Pokud zadáte název, který již existuje v knihovně, rozhraní IDE zobrazí chybovou zprávu.

Pokud váš projekt zásady vytváření názvů vyžaduje, abyste použili existující název, pak můžete pouze změnit velikost jeden nebo více písmen v názvu protože C++ je velká a malá písmena. Například i když nelze pojmenovat třídu `CDocument`, můžete ji nazvat `cdocument`.

## <a name="what-kind-of-class-do-you-want-to-add"></a>Jaký druh třídy chcete přidat?

V **přidat třídu** dialogové okno, když rozšiřujete **Visual C++** uzlu v levém podokně se zobrazí několik seskupení nainstalovaných šablon. Zahrnout skupiny **CLR**, **ATL**, **MFC**, a **C++**. Když vyberete skupinu, se v prostředním podokně zobrazí seznam dostupných šablon v této skupině. Každá šablona obsahuje soubory a zdrojový kód, který se vyžadují pro třídu.

Pokud chcete vygenerovat novou třídu, v prostředním podokně vyberte šablonu, zadejte název pro třídu v **název** pole a klikněte na tlačítko **přidat**. Tím se otevře **Průvodce přidáním třídy** tak, aby můžete určit možnosti pro třídu.

- Další informace o tom, jak vytvořit třídy knihovny MFC naleznete v tématu [třídy knihovny MFC](../mfc/reference/adding-an-mfc-class.md).

- Další informace o tom, jak vytvořit třídy ATL naleznete v tématu [jednoduchý objekt knihovny ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
>  Šablona **přidat podporu ATL do MFC** nevytváří žádné třídy, ale místo toho nakonfiguruje projekt, který používá knihovnu ATL. Další informace najdete v tématu [podpory knihovny ATL v projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Chcete-li vytvořit třídu C++, které nepoužívají knihovnu MFC, ATL nebo CLR, použijte **třídy C++** šablony **C++** skupiny nainstalovaných šablon. Další informace najdete v tématu [Přidání generické třídy jazyka C++](../ide/adding-a-generic-cpp-class.md).

Jsou k dispozici dva druhy založené na formulářích třídy jazyka C++. První z nich, [třídy CFormView](../mfc/reference/cformview-class.md) vytvoří třídy knihovny MFC. Je druhý řádek vytvoří třídu CLR Windows Forms.

## <a name="see-also"></a>Viz také

[Vytvoření aplikace MFC založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md)<br>
[Dialogové okno Přidat třídu](../ide/add-class-dialog-box.md)<br>
[Tvorba desktopových projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)