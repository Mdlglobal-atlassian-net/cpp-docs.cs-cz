---
title: Stránky vlastností nástroje Generátor dokumentů XML | Microsoft Docs
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
ms.openlocfilehash: 772e9dc6a296873ef27171676ebca0c185c1771c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339073"
---
# <a name="xml-document-generator-tool-property-pages"></a>Stránky vlastností nástroje Generátor dokumentů XML
Stránka vlastností nástroje Generátor dokumentů XML zpřístupní funkce xdcmake.exe. xdcmake.exe slučuje soubory do souboru .xml při zdrojový kód obsahuje komentáře a [/DOC (zpracování dokumentačních komentářů) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) je zadán. V tématu [doporučené značky pro dokumentační komentáře](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) informace o přidání komentáře dokumentace ke zdrojovému kódu.  
  
> [!NOTE]
>  Možnosti xdcmake.exe ve vývojovém prostředí (stránky vlastností) liší z možností při xdcmake.exe se používá v příkazovém řádku. Informace o použití xdcmake.exe příkazového řádku najdete v tématu [referenční dokumentace nástroje XDCMake](../ide/xdcmake-reference.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Potlačit úvodní nápis při spouštění**  
 Potlačíte zpráva o autorských právech.  
  
 **Další soubory dokumentu**  
 Další adresáře, ve kterých chcete projekt systému vyhledá soubory. xdcmake vždy vyhledá soubory projektu. Můžete zadat několik adresářů.  
  
 **Výstupní soubor dokumentu**  
 Název a umístění výstupního souboru .xml. V tématu [běžné makra pro příkazy sestavení a vlastnosti](../ide/common-macros-for-build-commands-and-properties.md) informace o použití maker pro určení umístění adresářů.  
  
 **Závislosti knihovny dokumentů**  
 Pokud váš projekt má závislost na .lib projektu v řešení, můžete zpracovat soubory z projektu .lib do souborů .xml aktuálního projektu.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)   
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)