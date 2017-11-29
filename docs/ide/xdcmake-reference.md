---
title: "Referenční dokumentace nástroje XDCMake | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xdcmake
dev_langs: C++
helpviewer_keywords: xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad0744da891c93dab44c980ed10aa4213a4dddb3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="xdcmake-reference"></a>Referenční dokumentace nástroje XDCMake
xdcmake.exe je program, který se zkompiluje soubory do souboru .xml. Projektový soubor je vytvoří – kompilátor Visual C++ pro každého souboru se zdrojovým kódem, když zdrojový kód je kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) a když souboru se zdrojovým kódem obsahuje označené značky XML – dokumentační komentáře.  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Chcete-li použít xdcmake.exe ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
2.  Otevřete **vlastnosti konfigurace** složky.  
  
3.  Klikněte **komentářů k dokumentu XML** stránku vlastností.  
  
> [!NOTE]
>  Při xdcmake.exe se používá ve vývojovém prostředí (stránky vlastností), se liší od možnosti xdcmake.exe možnosti příkazového řádku. Informace o použití xdcmake.exe ve vývojovém prostředí najdete v tématu [stránky vlastností nástroje Generátor dokumentů XML](../ide/xml-document-generator-tool-property-pages.md).  
  
## <a name="syntax"></a>Syntaxe  
 xdcmake`input_filename options`  
  
## <a name="parameters"></a>Parametry  
 kde:  
  
 `input_filename`  
 Název souboru používá jako vstup pro xdcmake.exe soubory. Zadejte jeden nebo více soubory nebo použijte *.xdc používat všechny soubory v aktuálním adresáři.  
  
 `options`  
 Nula nebo více následujících akcí:  
  
|Možnost|Popis|  
|------------|-----------------|  
|/?, / help|Zobrazit nápovědu pro xdcmake.exe.|  
|/Assembly:*filename*|Umožňuje zadat hodnotu \<sestavení > značky v souboru .xml.  Výchozí hodnota \<sestavení > Značka je stejný jako název souboru .xml.|  
|/nologo|Potlačíte zpráva o autorských právech.|  
|/ out:*filename*|Umožňuje zadat název souboru .xml.  Ve výchozím nastavení je název souboru .xml název souboru zpracovává xdcmake.exe první projektový soubor.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Studio bude vyvolán xdcmake.exe automaticky při sestavení projektu. Můžete také vyvolat xdcmake.exe na příkazovém řádku.  
  
 V tématu [doporučené značky pro dokumentační komentáře](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) pro další informace o přidání komentáře dokumentace pro soubory zdrojového kódu.  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)