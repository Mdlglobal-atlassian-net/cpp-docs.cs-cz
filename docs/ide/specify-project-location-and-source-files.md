---
title: Nový projekt z existujícího kódu – zdrojové soubory (Visual C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 3647ad3211043a5356649cb5f350ec07009f2279
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707834"
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>Zadání umístění projektu a zdrojových souborů, Průvodce vytvořením nového projektu z existujících souborů kódu
Tato stránka Průvodce vytvoření nového projektu z existujících souborů kódu slouží k určení:  
  
-   Cesta k adresáři nového projektu  
  
-   Adresáře ke hledání pro zdrojové soubory  
  
-   Typy souborů, které průvodce provede import do nového projektu  
  
## <a name="task-list"></a>Seznam úloh  
[Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
- **Umístění souboru projektu**

   Určuje cestu k adresáři nový projekt. Toto umístění je, kde průvodce uloží všechny soubory (a jeho podadresářích) nového projektu.  
  
- **Procházet**

   Zobrazí **umístění souboru projektu** dialogové okno, které vám umožní určit adresář, který bude obsahovat nový projekt. Tento ovládací prvek umožňuje přejděte do požadované složky.  
  
- **název projektu**

   Určuje název nového projektu. Soubory projektu, které mají přípony, jako je tento název přijmou .vcxproj. Existujících souborů kódu se zachovají původní názvy.  
  
- **Přidejte soubory do projektu z těchto složek**

   Pokud je zaškrtnuto, nastaví průvodcem ke kopírování existujících souborů kódu z jejich původní adresářů (které jsou uvedeny v seznamu pod tento ovládací prvek) do nového projektu.  
  
- **Přidat podsložky**

   Určuje, zkopírujte soubory kódu ze všech podadresářích adresáře uvedené **složky** sloupce do nového projektu.  
  
- **Složka**

   Určuje cestu k adresáři, který obsahuje existujících souborů kódu, který se zkopíruje do nového projektu. V tomto sloupci jsou uvedeny všechny adresáře, které průvodce vyhledá existujících souborů kódu.  
  
- **Add**

   Zobrazí **přidat soubory do projektu z této složky** dialogové okno, které vám pomůže určit adresáře, které průvodce vyhledá existujících souborů kódu.  
  
- **odebrat**

   Odstraní cesta k adresáři, který je vybrán v seznamu nalevo tohoto ovládacího prvku.  
  
- **Typy souborů, které chcete přidat do projektu**

   Určuje typy souborů, které průvodce přidá do nový projekt založený na daný soubor rozšíření. Přípony souborů jsou uvedeny s zástupný znak hvězdička a jsou odděleny středníky v seznamu přípon souborů.  
  
- **Zobrazit všechny soubory v Průzkumníku řešení**

   Určuje, že všechny soubory v novém projektu bude viditelné a zobrazují se v okně Průzkumník řešení. Tato možnost je povolená ve výchozím nastavení.