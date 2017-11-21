---
title: "Vytvoření aplikace kontejnerů pro aktivní dokument | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 66618fd86d1ced689cffbaeef3da08cc0c0491a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-an-active-document-container-application"></a>Vytvoření aplikace kontejnerů pro aktivní dokument
Většina doporučený a nejjednodušší způsob, jak vytvořit aplikace kontejnerů pro aktivní dokument je vytvoření kontejneru aplikace MFC EXE pomocí Průvodce aplikací knihovny MFC a pak upravit aplikaci, aby podporovala obsahování pro aktivní dokument.  
  
#### <a name="to-create-an-active-document-container-application"></a>K vytvoření aplikace kontejnerů pro aktivní dokument  
  
1.  Z **souboru** nabídky, klikněte na tlačítko **projektu**z **nový** podnabídky.  
  
2.  V levém podokně klikněte na tlačítko **Visual C++** typ projektu.  
  
3.  Vyberte **aplikace knihovny MFC** v pravém podokně.  
  
4.  Název projektu `MyProj`, klikněte na tlačítko **OK**.  
  
5.  Vyberte **složené podporu dokumentu** stránky.  
  
6.  Vyberte **kontejneru** nebo **kontejner/úplný server** možnost.  
  
7.  Vyberte **kontejner pro aktivní dokument** zaškrtávací políčko.  
  
8.  Klikněte na tlačítko **Dokončit**.  
  
9. Po dokončení Průvodce aplikací MFC generování aplikace, otevřete následující soubory pomocí Průzkumníku řešení:  
  
    -   MyProjview.cpp  
  
10. V MyProjview.cpp proveďte následující změny:  
  
    -   V `CMyProjView::OnPreparePrinting`, obsah funkce nahraďte následujícím kódem:  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting`poskytuje podporu tisku. Tento kód nahrazuje `DoPreparePrinting`, což je výchozí tiskové přípravy.  
  
     Obsahování pro aktivní dokument poskytuje vylepšené tisk schéma:  
  
    -   Nejprve můžete volat aktivní dokument pomocí jeho `IPrint` rozhraní a určit, aby sám sebe tisku. To se liší od předchozí OLE členství ve skupině, ve kterém měl kontejner k vykreslení image obsažený položky do tiskárny `CDC` objektu.  
  
    -   Pokud to nepomůže, řekněte obsažené položka tisknout samotné prostřednictvím jeho `IOleCommandTarget` rozhraní  
  
    -   Pokud to nepomůže, zkontrolujte vlastní vykreslování položky.  
  
     Statické členské funkce `COleDocObjectItem::OnPrint` a `COleDocObjectItem::OnPreparePrinting`, jak jsou implementované v předchozí kód zpracování této vylepšené schéma tisku.  
  
11. Přidejte všechny vlastní implementaci a sestavení aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Obsahování pro aktivní dokument](../mfc/active-document-containment.md)

