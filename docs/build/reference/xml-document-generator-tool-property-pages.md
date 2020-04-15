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
ms.openlocfilehash: d17913909532c5bebcac712937af00be3ad98712
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335769"
---
# <a name="xml-document-generator-tool-property-pages"></a>Stránky vlastností nástroje Generátor dokumentů XML

Stránka vlastností Nástroje generátoru dokumentů XML zpřístupňuje funkce nástroje xdcmake.exe. xdcmake.exe slučuje soubory .xdc do souboru XML, pokud zdrojový kód obsahuje komentáře k dokumentaci a [/doc (Process Documentation Comments) (C/C++)](doc-process-documentation-comments-c-cpp.md) je zadáno.. Informace o přidávání poznámek k dokumentaci do zdrojového kódu najdete v části [Doporučené značky pro komentáře k dokumentaci.](recommended-tags-for-documentation-comments-visual-cpp.md)

> [!NOTE]
> možnosti xdcmake.exe ve vývojovém prostředí (stránky vlastností) se liší od možností při použití nástroje xdcmake.exe na příkazovém řádku. Informace o použití příkazu xdcmake.exe na příkazovém řádku naleznete v tématu [XDCMake Reference](xdcmake-reference.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Potlačit spouštěcí banner**

   Potlačit zprávu o autorských právech.

- **Další soubory dokumentů**

   Další adresáře, ve kterých má systém projektu hledat soubory XDC. xdcmake bude vždy hledat .xdc soubory generované projektem. Lze zadat více adresářů.

- **Výstupní soubor dokumentu**

   Název a umístění adresáře výstupního souboru XML. Informace o použití maker k určení umístění adresářů naleznete [v tématu Společná makra pro příkazy a vlastnosti sestavení.](common-macros-for-build-commands-and-properties.md)

- **Závislosti knihovny dokumentů**

   Pokud je projekt závislý na projektu LIB v řešení, můžete zpracovat soubory .xdc z projektu LIB do souborů XML pro aktuální projekt.

## <a name="see-also"></a>Viz také

[Odkaz na stránku vlastnosti projektu jazyka C++](property-pages-visual-cpp.md)
