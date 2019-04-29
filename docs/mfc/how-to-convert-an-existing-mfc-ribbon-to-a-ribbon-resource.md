---
title: 'Postupy: Převod existujícího pásu karet MFC na prostředek pásu karet'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: b4265a7bf3ebe2c4926f21572d802b75bd525990
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389486"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Postupy: Převod existujícího pásu karet MFC na prostředek pásu karet

Prostředky z pásu karet se snadněji vizualizovat, změnit a udržovat než ručně kódovaný pásů karet. Toto téma popisuje, jak převést ručně kódovaný pás karet v projektu knihovny MFC na prostředek pásu karet.

Musíte mít existující projekt knihovny MFC, která má kód, který používá třídy pásu karet MFC, například [CMFCRibbonBar – třída](../mfc/reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Převést pásu karet MFC na prostředek pásu karet

1. V sadě Visual Studio v existujícím projektu knihovny MFC, otevřete zdrojový soubor kde `CMFCRibbonBar` objekt je inicializován. Soubor je obvykle mainfrm.cpp. Přidejte následující kód za kód inicializace pro pás karet.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   Soubor uložte a zavřete.

1. Sestavení a spuštění aplikace knihovny MFC v poznámkovém bloku otevřete RibbonOutput.txt a zkopírujte jeho obsah.

1. V sadě Visual Studio na **projektu** nabídky, klikněte na tlačítko **přidat prostředek**. V **přidat prostředek** dialogu **pásu karet** a potom klikněte na tlačítko **nový**.

   Visual Studio vytvoří prostředek pásu karet a otevře v zobrazení návrhu. ID prostředku pásu karet je IDR_RIBBON1, který se zobrazí v **zobrazení prostředků**. Na pásu karet je definována v souboru XML ribbon1.mfcribbon ms.

1. V sadě Visual Studio otevřete ribbon1.mfcribbon ms, odstraňte její obsah a vložte obsah RibbonOutput.txt, který jste si zkopírovali dříve. Uložte a zavřete ribbon1.mfcribbon ms.

1. Znovu otevřete zdrojový soubor, ve kterém je inicializován CMFCRibbonBar – objekt (obvykle mainfrm.cpp) a Odkomentujte existující kód pásu karet. Přidejte následující kód za kód, který je označené jako komentář.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. Sestavte projekt a spusťte program.

## <a name="see-also"></a>Viz také:

[Návrhář pásu karet (MFC)](../mfc/ribbon-designer-mfc.md)
