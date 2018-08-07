---
title: 'Postupy: Import a Export prostředků | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [Visual Studio], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49cdee9cfed3b5694fcea899b9250c5f9dd214b7
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570477"
---
# <a name="how-to-import-and-export-resources"></a>Postupy: Import a export prostředků
Můžete importovat grafických prostředků (rastrové obrázky, ikony, kurzory a panely nástrojů), soubory HTML a vlastní prostředky pro použití v jazyce Visual C++. Stejné typy souborů, můžete exportovat z projektu Visual C++ do samostatných souborů, které lze použít mimo vývojové prostředí.  
  
> [!NOTE]
>  Typy prostředků jako akcelerátory, dialogová okna a tabulky řetězců nelze importovaná nebo exportovaná, protože nejsou typy samostatný soubor.  
  
### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Importovat jednotlivé prostředky do aktuálního souboru prostředků  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na uzel pro skript prostředků (* .rc) soubor, ke kterému chcete přidat prostředek.  
  
2.  Klikněte na tlačítko **Import** v místní nabídce.  
  
3.  Vyhledejte a vyberte název souboru rastrový obrázek (BMP), ikona (), kurzor (), soubor Html (.htm) nebo jiný soubor, který chcete importovat.  
  
4.  Klikněte na tlačítko **OK** bude příslušný materiál přidán na vybraný soubor v **prostředků** zobrazení.  
  
    > [!NOTE]
    >  Proces importu funguje stejným způsobem bez ohledu na to, který prostředek se konkrétní typ jste vybrali. Importovaných zdrojů je automaticky přidán do správný uzel pro příslušný typ prostředku.  
  
### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Chcete-li exportovat bitmapy, ikony nebo kurzoru jako samostatný soubor (pro použití mimo aplikaci Visual C++)  
  
1.  V **prostředků** zobrazení, klikněte pravým tlačítkem na prostředku, kterou chcete exportovat.  
  
2.  Klikněte na tlačítko **exportovat** v místní nabídce.  
  
3.  V **exportovat prostředky** dialogové okno pole názvu aktuálního souboru přijměte nebo zadejte nový.  
  
4.  Přejděte do složky, kam chcete uložit soubor a klikněte na tlačítko **exportovat**.  
  
## <a name="requirements"></a>Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)