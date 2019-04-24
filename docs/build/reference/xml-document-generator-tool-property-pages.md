---
title: Stránky vlastností nástroje Generátor dokumentů XML
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
ms.openlocfilehash: c99677d7fc53ae3343e15e54997fe0101322fbcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316155"
---
# <a name="xml-document-generator-tool-property-pages"></a>Stránky vlastností nástroje Generátor dokumentů XML

Stránka vlastností nástroje Generátor dokumentů XML zpřístupňuje funkce xdcmake.exe. xdcmake.exe souborech .xdc sloučí do souboru .xml, když váš zdrojový kód obsahuje komentáře k dokumentaci a [/DOC (zpracování dokumentačních komentářů) (C/C++)](doc-process-documentation-comments-c-cpp.md) je zadán. Zobrazit [doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments-visual-cpp.md) informace o přidání komentáře k dokumentaci ke zdrojovému kódu.

> [!NOTE]
>  Možnosti xdcmake.exe ve vývojovém prostředí (stránky vlastností) se liší od možností xdcmake.exe zadáním na příkazovém řádku. Informace o používání xdcmake.exe příkazového řádku najdete v tématu [referenční dokumentace nástroje XDCMake](xdcmake-reference.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Potlačit úvodní nápis**

   Potlačí zprávu o autorských právech.

- **Další soubory dokumentu**

   Další adresáře, ve kterých se má systém projektu souborů .xdc. xdcmake – bude vždy hledat soubory v projektu. Je možné zadat více adresářů.

- **Výstupní soubor dokumentu**

   Název a umístění výstupního souboru XML. Zobrazit [sestavení běžná makra pro příkazy a vlastnosti](common-macros-for-build-commands-and-properties.md) informace o použití maker k určení umístění adresáře.

- **Závislosti knihoven dokumentu**

   Pokud váš projekt obsahuje závislost na lib projekt v řešení, může zpracovat soubory z projektu .lib do souborů .xml pro aktuální projekt.

## <a name="see-also"></a>Viz také:

[Odkaz na stránku vlastností projektu jazyka C++](property-pages-visual-cpp.md)