---
title: "Chyba sestavení projektu PRJ0003 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0003
dev_langs: C++
helpviewer_keywords: PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f06779fb8f2d5265d93cc4376b42669b978c4e5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0003"></a>Chyba sestavení projektu PRJ0003  
  
> Chyba při vytváření kopie '*příkazového řádku*'.  
  
*Příkazového řádku* příkaz vytvořen ze vstupu v **stránky vlastností** dialogové okno vrátilo kód chyby, ale žádné informace se zobrazí v **výstup** okno.  

Možné důvody této chyby patří:  
  
-   Projekt závisí na ATL Server. Od verze Visual Studio 2008, ATL Server již není součástí sady Visual Studio, ale byla vydána jako sdílený zdroj projekt na webu CodePlex. Chcete-li stáhnout ATL Server zdrojového kódu a nástroje, přejděte na [knihovny serveru ATL Server a nástroje](http://go.microsoft.com/fwlink/?LinkID=81979).  
  
-   Nedostatek systémových prostředků. Zavřete některé aplikace, abyste tento problém vyřešili.  
  
-   Nedostatečná oprávnění. Ověřte, zda máte dostatečná oprávnění.  
  
-   Spustitelný soubor cesty zadané v **adresáře VC ++** neobsahují cestu pro nástroj, který se pokoušíte spustit. Informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)  
  
-   Pro projekty makefile chybí příkaz ke spuštění na buď **sestavení příkazového řádku** nebo **opětovné sestavení příkazového řádku**.  
  
## <a name="see-also"></a>Viz také  
 [Chyby sestavení a upozornění projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)