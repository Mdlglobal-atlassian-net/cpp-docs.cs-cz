---
title: Vytváření aplikací MFC založených na formulářích
ms.date: 09/09/2019
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: 1dbbc5c29f85ced846cb3e07a02a5d6a55c94b20
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908056"
---
# <a name="creating-a-forms-based-mfc-application"></a>Vytváření aplikací MFC založených na formulářích

Formulář je dialogové okno s ovládacími prvky, které uživateli umožňují přístup a případně mění data. Možná budete chtít vyvinout aplikaci, ve které uživatel vybere výběr formulářů. Aplikace založené na formulářích obvykle umožňují uživatelům přístup pomocí formulářů kliknutím na **Nový** v nabídce **soubor** . Dialogová aplikace, která nedává uživatelům přístup k **nové** možnosti v nabídce **soubor** , je také považována za aplikaci založenou na formulářích.

Rozhraní Single Document Interface (SDI), aplikace založená na formulářích, umožňuje spuštění pouze jedné instance konkrétního formuláře. Můžete spouštět různé formuláře současně z aplikace založené na formulářích SDI výběrem nového formuláře z možnosti **Nový** v nabídce **soubor** .

Pokud vytvoříte rozhraní MDI (Multiple Document Interface), aplikace založené na formulářích, aplikace bude moci podporovat více instancí stejné formy.

Vytvoříte-li aplikaci s více podporou dokumentu nejvyšší úrovně, je plocha implicitním nadřazeným objektem pro dokument a rámec dokumentu není omezen na klientskou oblast aplikace. Můžete otevřít více instancí dokumentu, z nichž každá má vlastní rámeček, nabídku a ikonu na hlavním panelu. Další instance dokumentů můžete zavřít jednotlivě, ale pokud vyberete možnost **ukončit** v nabídce **soubor** počáteční instance, aplikace zavře všechny instance.

Aplikace SDI, MDI a více aplikací dokumentu nejvyšší úrovně jsou založeny na formulářích a používají architekturu document/view.

Každá aplikace založená na dialogu, podle definice, je založena na formulářích. Dialogová aplikace nepoužívá architekturu document/view, takže musíte spravovat metody vytváření a přístupu pro vlastní další formuláře.

Základní třída pro aplikace založené na formulářích je [CFormView](cformview-class.md). Pokud má vaše aplikace podporu databáze, můžete také vybrat libovolnou třídu, která je odvozena z `CFormView`. Formulář je jakékoli okno odvozené z `CFormView` nebo z libovolné třídy, ze `CFormView`které dědí.

I v případě, že použijete základní třídu, jako je například [CView](cview-class.md), můžete později vytvořit své aplikace na základě [Přidání třídy knihovny MFC](adding-an-mfc-class.md) odvozené `CFormView`z.

Po dokončení průvodce se projekt otevře a pokud jste vybrali `CFormView` (nebo třídu, která dědí z `CFormView`) jako základní třídu, nebo pokud jste vytvořili dialogovou aplikaci, vizuál C++ otevře Editor dialogových oken. V tuto chvíli jste připraveni navrhnout první formulář.

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Chcete-li začít vytvářet spustitelný soubor MFC založený na formulářích

1. Postupujte podle pokynů v části [Vytvoření aplikace MFC](creating-an-mfc-application.md) pro aplikaci MFC založenou na formulářích.

1. Na stránce [Typ aplikace](application-type-mfc-application-wizard.md) Průvodce aplikací knihovny MFC vyberte zaškrtávací políčko **Podpora architektury dokument/zobrazení** .

1. Vyberte **jeden dokument**, **více dokumentů**nebo **více dokumentů nejvyšší úrovně**.

    > [!NOTE]
    >  Pokud jste zvolili aplikaci SDI, MDI nebo více aplikací rozhraní dokumentu nejvyšší úrovně, `CView` je ve výchozím nastavení nastavena jako základní třída pro zobrazení vaší aplikace na stránce [vygenerované třídy](generated-classes-mfc-application-wizard.md) v průvodci. Chcete-li vytvořit aplikaci založenou na formulářích, je `CFormView` nutné vybrat jako základní třídu pro zobrazení aplikace. Všimněte si, že Průvodce neposkytuje podporu tisku pro aplikace založené na formulářích.

1. Na ostatních stránkách průvodce nastavte další požadované možnosti projektu.

1. Vytvořte kostru aplikace kliknutím na tlačítko **Dokončit** .

Další informace naleznete v tématu:

- [Odvozené třídy zobrazení](../derived-view-classes-available-in-mfc.md)

- [Alternativy k architektuře Document/View](../alternatives-to-the-document-view-architecture.md)

- [Volby při návrhu aplikací](../application-design-choices.md)

## <a name="see-also"></a>Viz také:

[MFC – průvodce aplikací](mfc-application-wizard.md)<br/>
[Zobrazení formulářů](../form-views-mfc.md)<br/>
[Vytvoření aplikace MFC ve stylu Průzkumníka souborů](creating-a-file-explorer-style-mfc-application.md)<br/>
[Vytvoření aplikace MFC ve stylu webového prohlížeče](creating-a-web-browser-style-mfc-application.md)
