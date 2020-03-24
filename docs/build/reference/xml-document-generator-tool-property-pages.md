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
ms.openlocfilehash: 9f10ddf98c238120750e72644779a6ad74af2d1e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171629"
---
# <a name="xml-document-generator-tool-property-pages"></a>Stránky vlastností nástroje Generátor dokumentů XML

Stránka vlastností nástroje generátor dokumentů XML zpřístupňuje funkce xdcmake. exe. xdcmake. exe sloučí soubory. xdc do souboru. XML, když váš zdrojový kód obsahuje dokumentační komentáře a [/doc (zpracování dokumentačních komentářů) (C/C++)](doc-process-documentation-comments-c-cpp.md) je zadán. Informace o přidávání komentářů k dokumentaci ke zdrojovému kódu naleznete v tématu [Doporučené značky pro dokumentační komentáře](recommended-tags-for-documentation-comments-visual-cpp.md) .

> [!NOTE]
>  možnosti xdcmake. exe ve vývojovém prostředí (stránky vlastností) se liší od možností při použití xdcmake. exe na příkazovém řádku. Informace o použití xdcmake. exe na příkazovém řádku naleznete v tématu [xdcmake reference](xdcmake-reference.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Potlačit úvodní nápis**

   Potlačit zprávu o autorských právech.

- **Další soubory dokumentů**

   Další adresáře, ve kterých má projektový systém hledat soubory. xdc. xdcmake bude vždy hledat soubory. xdc generované projektem. Je možné zadat více adresářů.

- **Výstupní soubor dokumentu**

   Název a umístění výstupního souboru. XML. Informace o použití maker k určení umístění adresářů najdete v tématu [společná makra pro příkazy a vlastnosti sestavení](common-macros-for-build-commands-and-properties.md) .

- **Závislosti knihoven dokumentů**

   Pokud má projekt závislost na projektu. lib v řešení, můžete zpracovat soubory. xdc z projektu. lib do souborů. XML pro aktuální projekt.

## <a name="see-also"></a>Viz také

[C++odkaz na stránku vlastností projektu](property-pages-visual-cpp.md)
