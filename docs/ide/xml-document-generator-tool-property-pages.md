---
title: Stránky vlastností nástroje Generátor dokumentů XML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
dev_langs:
- C++
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72756a97d9d840b09d4b207cf47fedd8cddc59d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430760"
---
# <a name="xml-document-generator-tool-property-pages"></a>Stránky vlastností nástroje Generátor dokumentů XML

Stránka vlastností nástroje Generátor dokumentů XML zpřístupňuje funkce xdcmake.exe. xdcmake.exe souborech .xdc sloučí do souboru .xml, když váš zdrojový kód obsahuje komentáře k dokumentaci a [/DOC (zpracování dokumentačních komentářů) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) je zadán. Zobrazit [doporučené značky pro dokumentační komentáře](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) informace o přidání komentáře k dokumentaci ke zdrojovému kódu.

> [!NOTE]
>  Možnosti xdcmake.exe ve vývojovém prostředí (stránky vlastností) se liší od možností xdcmake.exe zadáním na příkazovém řádku. Informace o používání xdcmake.exe příkazového řádku najdete v tématu [referenční dokumentace nástroje XDCMake](../ide/xdcmake-reference.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Potlačit úvodní nápis**

   Potlačí zprávu o autorských právech.

- **Další soubory dokumentu**

   Další adresáře, ve kterých se má systém projektu souborů .xdc. xdcmake – bude vždy hledat soubory v projektu. Je možné zadat více adresářů.

- **Výstupní soubor dokumentu**

   Název a umístění výstupního souboru XML. Zobrazit [běžné Macros for Build Commands and Properties](../ide/common-macros-for-build-commands-and-properties.md) informace o použití maker k určení umístění adresáře.

- **Závislosti knihoven dokumentu**

   Pokud váš projekt obsahuje závislost na lib projekt v řešení, může zpracovat soubory z projektu .lib do souborů .xml pro aktuální projekt.

## <a name="see-also"></a>Viz také

[Stránky vlastností](../ide/property-pages-visual-cpp.md)<br>
[Stránky vlastností](../ide/property-pages-visual-cpp.md)