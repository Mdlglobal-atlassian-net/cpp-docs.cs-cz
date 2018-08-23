---
title: 'Postupy: určení adresáře souborů k zahrnutí pro prostředky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directories [C++], specifying include paths for resources
- include files, specifying for resources
- resources [Visual Studio], including in projects
ms.assetid: d6a7c0f6-4810-4bb0-b4b7-7d2476a20ca2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: baa317610339e7073f2e829860e11ab15e66277e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611058"
---
# <a name="how-to-specify-include-directories-for-resources"></a>Postupy: Určení adresářů souborů k zahrnutí pro prostředky

### <a name="to-specify-include-directories-for-a-specific-rc-file"></a>Určení adresářů include pro konkrétní soubor .rc

1. Klikněte pravým tlačítkem na soubor .rc v Průzkumníku řešení a vyberte **vlastnosti** z místní nabídky.

2. V **stránky vlastností** dialogové okno, klikněte na tlačítko **prostředky** uzlu v levém podokně, pak zadejte další adresáře include **další adresáře souborů k zahrnutí** Vlastnost.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v rozhraní .NET Framework Developer's Guide. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Prostředek zahrnuje – dialogové okno](../windows/resource-includes-dialog-box.md)  
[TN035: Použití více zdrojových souborů a hlavičkových souborů v jazyku Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)