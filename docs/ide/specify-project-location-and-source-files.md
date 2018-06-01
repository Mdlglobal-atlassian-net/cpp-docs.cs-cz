---
title: Nový projekt z existujícího kódu – zdrojové soubory (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.location
dev_langs:
- C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d85a7b85996ed307596865a31d55cf4b119e5bd5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33338692"
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>Zadání umístění projektu a zdrojových souborů, Průvodce vytvořením nového projektu z existujících souborů kódu
Na této stránce Průvodce vytvoření nového projektu z existujících souborů kódu můžete zadat:  
  
-   Cesta k adresáři nového projektu  
  
-   Adresáře k vyhledání existujícího zdrojové soubory  
  
-   Typy souborů, které průvodce provede import do nového projektu  
  
## <a name="task-list"></a>Seznam úloh  
 [Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Umístění souboru projektu**  
 Určuje cestu k adresáři nový projekt. Toto umístění je, kde průvodce uloží všechny soubory (a podadresáře) nového projektu.  
  
 **Procházet**  
 Zobrazí **umístění souboru projektu** dialog, který slouží k určení adresáře, který bude obsahovat nový projekt. Tento ovládací prvek umožňuje přejděte do požadované složky.  
  
 **název projektu**  
 Určuje název nového projektu. Soubory projektu, které mají přípony jako VCXPROJ zavede tento název. Existujících souborů kódu ponechá jejich původní název.  
  
 **Do projektu přidejte soubory z těchto složek**  
 Pokud je zaškrtnuto, nastaví průvodcem ke kopírování existujících souborů kódu z jejich původní adresáře (které jsou určené v poli seznamu níže tento ovládací prvek) do nového projektu.  
  
 **Přidat podsložky**  
 Určuje, zkopírujte soubory kódu z všechny podadresáře adresáře uvedené **složky** sloupce do nového projektu.  
  
 **Složka**  
 Určuje cestu k adresáři, který obsahuje existujících souborů kódu chcete zkopírovat do nového projektu. Tento sloupec uvádí všechny adresáře, které průvodce vyhledá existujících souborů kódu.  
  
 **Přidat**  
 Zobrazí **do projektu přidejte soubory z této složky** dialogové okno, které vám umožní určit adresáře, které průvodce vyhledá existujících souborů kódu.  
  
 **Odebrat**  
 Odstraní cesta k adresáři, který je vybraný v seznamu nalevo tohoto ovládacího prvku.  
  
 **Typy souborů, které chcete přidat do projektu**  
 Určuje typy souborů, které průvodce přidá do nového projektu založené na rozšířeních daný soubor. Přípony souborů jsou uvedeny s zástupný znak hvězdička a jsou v seznamu přípon souborů oddělený středníkem.  
  
 **Zobrazit všechny soubory v Průzkumníkovi řešení**  
 Určuje, že všechny soubory v novém projektu budou viditelné a zobrazených v okně Průzkumníka řešení. Tato možnost je povolená ve výchozím nastavení.