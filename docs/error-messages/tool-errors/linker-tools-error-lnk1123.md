---
title: "Chyba linkerů Lnk1123 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1123
dev_langs: C++
helpviewer_keywords: LNK1123
ms.assetid: fe47af69-0f42-4792-9133-541192cd8514
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ade68d51125167c34fc46f23a7c9ce7eccfdef5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1123"></a>Chyba linkerů LNK1123
Chyba při převodu do COFF: neplatný nebo poškozený soubor  
  
 Vstupní soubory musí mít formát běžné objekt souboru formátu (COFF). Pokud vstupní soubor není COFF, linkeru automaticky pokusí převést objekty OMF 32-bit do COFF, nebo se spouští CVTRES. EXE převést soubory prostředků. Tato zpráva znamená, že linkeru nebylo možné převést soubor. To může dojít také při použití nekompatibilní verze souboru CVTRES. EXE z jiné instalace sady Visual Studio, Windows Development Kit nebo rozhraní .NET Framework.  
  
> [!NOTE]
>  Pokud používáte starší verze sady Visual Studio, nemusí být podporována automatický převod.  
  
### <a name="to-fix-the-problem"></a>Vyřešte problém  
  
-   Použijte pro všechny aktualizace service Pack a aktualizace pro vaši verzi sady Visual Studio. To je obzvláště důležité pro Visual Studio 2010.  
  
-   Opakujte sestavení s přírůstkové propojování zakázáno. Na řádku nabídek zvolte **projektu**, **vlastnosti**. V **stránky vlastností** dialogové okno, rozbalte seznam **vlastnosti konfigurace**, **Linkeru**. Změňte hodnotu **Povolit přírůstkové propojování** k **ne**.  
  
-   Ověřte, že verze nástroje CVTRES. EXE nalezen nejprve vaše proměnná prostředí PATH odpovídá verzi nástroje pro sestavení nebo verzi sady nástrojů platformy použitou vaším projektem.  
  
-   Zkuste vypnout možnost vložení manifestu. Na řádku nabídek zvolte **projektu**, **vlastnosti**. V **stránky vlastností** dialogové okno, rozbalte seznam **vlastnosti konfigurace**, **Nástroj Manifest**, **vstup a výstup**. Změňte hodnotu **vložení manifestu** k **ne**.  
  
-   Ujistěte se, že je platný typ souboru. Například se ujistěte, že objekt OMF je 32bitová verze a nebyl 16 bitů. Další informace najdete v tématu [. Soubory obj jako vstup Linkeru](../../build/reference/dot-obj-files-as-linker-input.md) a [Microsoft PE a specifikace COFF](http://go.microsoft.com/fwlink/p/?LinkId=93292).  
  
-   Ujistěte se, že soubor není poškozen. Obnovit, v případě potřeby.  
  
## <a name="see-also"></a>Viz také  
 [. Soubory obj jako vstup Linkeru](../../build/reference/dot-obj-files-as-linker-input.md)   
 [Editbin – odkaz](../../build/reference/editbin-reference.md)   
 [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md)