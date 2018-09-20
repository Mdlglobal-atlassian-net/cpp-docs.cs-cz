---
title: Vytvoření aplikace MFC založené na formulářích | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcforms.project
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 692370e06668152cb6f5d5ecc762a3bbe991af08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374654"
---
# <a name="creating-a-forms-based-mfc-application"></a>Vytváření aplikací MFC založených na formulářích

Formulář je dialogové okno s ovládacími prvky, které mohl uživatel získávat přístup a pravděpodobně měnit data. Můžete vyvíjet aplikace, ve kterém uživatel vybere z výběru formuláře. Aplikace založené na formulářích často, umožní uživateli přístup k formulářům kliknutím **nový** z **souboru** nabídky. Dialogové okno aplikace, které uživateli neposkytují přístup k **nový** možnost **souboru** nabídky, jsou také považovány za aplikace založené na formulářích.

Rozhraní jednoho dokumentu (SDI), aplikace založené na formulářích umožňuje pouze jednu instanci příslušného formuláře ke spuštění v čase. Je možné spustit různé formuláře ve stejnou dobu z aplikace založené na formulářích SDI tak, že vyberete nového formuláře pomocí **nový** možnost **souboru** nabídky.

Pokud vytvoříte rozhraním více dokumentů (MDI), aplikace založené na formulářích, aplikace bude moci podporovat více instancí stejného formuláře.

Pokud vytvoříte aplikaci s podporou více dokumentů nejvyšší úrovně, je implicitní nadřazené dokumentu a rámce dokumentu se neomezuje na oblasti klienta aplikace. Můžete otevřít více instance dokumentu, každá má svou vlastní rámce, nabídky a ikonu panelu úloh. Můžete zavřít další instance dokumenty jednotlivě, ale pokud vyberete **ukončovací** možnost **souboru** nabídka původní instance, aplikace se zavře všechny instance.

SDI, MDI a více nejvyšší úrovně dokumentu aplikace jsou všechny formuláře na základě a použít architekturu document/view.

Všechny aplikace založené na dialogu, podle definice je na základě formulářů. Aplikace založené na dialogu architekturu document/view nepoužívá, takže je třeba spravovat metody vytvoření a přístupu pro další formulářů.

Základní třída pro aplikace založené na formulářích je [CFormView](../../mfc/reference/cformview-class.md). Pokud má vaše aplikace Podpora databáze, pak můžete také vybrat jakoukoli třídu, která je odvozena z `CFormView`. Formulář je jakékoli okno odvozené od `CFormView` nebo z jiné třídy, která dědí z `CFormView`.

I v případě, že je použít jako základní třídu [CView](../../mfc/reference/cview-class.md), můžete později provést aplikace formulářů pomocí [přidání třídy knihovny MFC](../../mfc/reference/adding-an-mfc-class.md) odvozený od `CFormView` a kontrolu **generovat DocTemplate prostředky** zaškrtávací políčko ve [Průvodce třídami MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).

Po dokončení Průvodce vytvořením projektu se otevře, a pokud jste vybrali `CFormView` (nebo třídu, která dědí z `CFormView`) jako základní třída nebo pokud jste vytvořili aplikaci založené na dialogu, Visual C++ se otevře editor dialogového okna. V tuto chvíli jste připraveni k návrhu první formuláře.

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Můžete začít vytvářet založené na formulářích spustitelný soubor knihovny MFC

1. Postupujte podle pokynů v [vytvoření aplikace MFC](../../mfc/reference/creating-an-mfc-application.md).

1. Průvodce aplikací knihovny MFC [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránky, vyberte **podpora architektury Document/view** zaškrtávací políčko.

1. Vyberte **jednotlivý dokument**, **více dokumentů**, nebo **více dokumentů na nejvyšší úrovni**.

    > [!NOTE]
    >  Pokud jste zvolili SDI, MDI nebo rozhraní více dokumentů nejvyšší úrovně ve výchozím nastavení, `CView` je nastaven jako základní třída pro zobrazení vaší aplikace [třídy generované v](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránce průvodce. Vytvoření aplikace založené na formulářích, musíte vybrat `CFormView` jako základní třída pro zobrazení vaší aplikace. Všimněte si, že Průvodce neposkytuje podporu tisku pro aplikace založené na formulářích.

1. Nastavte další požadované možnosti projektu na dalších stránkách průvodce.

1. Klikněte na tlačítko **Dokončit** ke generování kostry aplikace.

Další informace naleznete v tématu:

- [Odvozené třídy zobrazení](../../mfc/derived-view-classes-available-in-mfc.md)

- [Alternativy k architektuře dokument/zobrazení](../../mfc/alternatives-to-the-document-view-architecture.md)

- [Volby při návrhu aplikací](../../mfc/application-design-choices.md)

## <a name="see-also"></a>Viz také

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)<br/>
[Zobrazení formulářů](../../mfc/form-views-mfc.md)<br/>
[Vytvoření aplikace MFC ve stylu Průzkumníka souborů](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)<br/>
[Vytvoření aplikace MFC ve stylu webového prohlížeče](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

