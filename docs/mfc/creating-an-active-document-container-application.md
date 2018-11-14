---
title: Vytvoření aplikace kontejnerů pro aktivní dokument
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 5cdd3de8f4efcc23f89b81cb61302b5950938800
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520410"
---
# <a name="creating-an-active-document-container-application"></a>Vytvoření aplikace kontejnerů pro aktivní dokument

Nejjednodušší a největší doporučený způsob, jak vytvořit aplikace kontejnerů pro aktivní dokument je vytvoření aplikace MFC EXE kontejner pomocí Průvodce aplikací knihovny MFC a pak upravit aplikaci, aby podporovala zahrnutí aktivního dokumentu.

#### <a name="to-create-an-active-document-container-application"></a>Vytvoření aplikace kontejnerů pro aktivní dokument

1. Z **souboru** nabídky, klikněte na tlačítko **projektu**z **nový** podnabídka.

1. V levém podokně klikněte na tlačítko **Visual C++** typ projektu.

1. Vyberte **aplikace knihovny MFC** v pravém podokně.

1. Pojmenujte projekt *MyProj*, klikněte na tlačítko **OK**.

1. Vyberte **Podpora složených dokumentů** stránky.

1. Vyberte **kontejneru** nebo **kontejner/úplný server** možnost.

1. Vyberte **kontejner pro aktivní dokument** zaškrtávací políčko.

1. Klikněte na tlačítko **Dokončit**.

1. Po dokončení Průvodce aplikací knihovny MFC generuje aplikaci otevřete následujících souborů pomocí Průzkumníka řešení:

   - *MyProjview.cpp*

1. V *MyProjview.cpp*, proveďte následující změny:

   - V `CMyProjView::OnPreparePrinting`, funkce obsah nahraďte následujícím kódem:

     [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` poskytuje podporu tisku. Tento kód nahradí `DoPreparePrinting`, což je výchozí Příprava tisku.

   Zahrnutí aktivního dokumentu poskytuje vylepšené schéma tisku:

   - Můžete nejprve volat aktivní dokument pomocí jeho `IPrint` rozhraní a určit, aby se vytiskl. Tím se liší od předchozí OLE členství ve skupině, ve kterém museli vykreslil obraz obsažené položky do tiskárny kontejneru `CDC` objektu.

   - Pokud selže, informace obsažené položky, aby se vytiskl prostřednictvím jeho `IOleCommandTarget` rozhraní

   - Pokud se nezdaří, zkontrolujte vlastní vykreslování položky.

   Statické členské funkce `COleDocObjectItem::OnPrint` a `COleDocObjectItem::OnPreparePrinting`, jak je implementován v předchozím kódu zpracovávat toto vylepšené schéma tisku.

1. Přidejte všechny vlastní implementaci a sestavte aplikaci.

## <a name="see-also"></a>Viz také

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

