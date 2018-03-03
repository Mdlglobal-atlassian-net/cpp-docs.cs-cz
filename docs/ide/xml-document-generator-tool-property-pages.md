---
title: "Stránky vlastností nástroje Generátor dokumentů XML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCXDCMakeTool.ValidateIntelliSense
- VC.Project.VCXDCMakeTool.SuppressStartupBanner
- VC.Project.VCXDCMakeTool.DocumentLibraryDependencies
- VC.Project.VCXDCMakeTool.OutputDocumentFile
- VC.Project.VCXDCMakeTool.AdditionalDocumentFiles
dev_langs:
- C++
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc09dafc0f07bc16a11dd255419440b6464456c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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