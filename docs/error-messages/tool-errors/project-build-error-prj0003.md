---
title: Chyba sestavení projektu PRJ0003 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0003
dev_langs:
- C++
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a44f272569741b1897caed1d1d64832d8b113eae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0003"></a>Chyba sestavení projektu PRJ0003  
  
> Chyba při vytváření kopie '*příkazového řádku*'.  
  
*Příkazového řádku* příkaz vytvořen ze vstupu v **stránky vlastností** dialogové okno vrátilo kód chyby, ale žádné informace se zobrazí v **výstup** okno.  

Možné důvody této chyby patří:  
  
-   Projekt závisí na ATL Server. Od verze Visual Studio 2008, ATL Server již není součástí sady Visual Studio, ale byla vydána jako sdílený zdroj projekt na webu CodePlex. Chcete-li stáhnout ATL Server zdrojového kódu a nástroje, přejděte na [knihovny serveru ATL Server a nástroje](http://go.microsoft.com/fwlink/p/?linkid=81979).  
  
-   Nedostatek systémových prostředků. Zavřete některé aplikace, abyste tento problém vyřešili.  
  
-   Nedostatečná oprávnění. Ověřte, zda máte dostatečná oprávnění.  
  
-   Spustitelný soubor cesty zadané v **adresáře VC ++** neobsahují cestu pro nástroj, který se pokoušíte spustit. Informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)  
  
-   Pro projekty makefile chybí příkaz ke spuštění na buď **sestavení příkazového řádku** nebo **opětovné sestavení příkazového řádku**.  
  
## <a name="see-also"></a>Viz také  
 [Chyby a upozornění sestavení projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)