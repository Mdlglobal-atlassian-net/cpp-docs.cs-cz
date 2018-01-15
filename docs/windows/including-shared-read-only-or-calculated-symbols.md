---
title: "Zahrnutí sdílených (jen pro čtení) nebo vypočtených symbolů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.shared.calculated
dev_langs: C++
helpviewer_keywords:
- symbols, read-only
- symbols, shared
- symbols, calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bf0beeb90e2d4c4d22f45322f881bb7a247acf12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>Zahrnutí sdílených (jen pro čtení) nebo vypočtených symbolů
Při prvním vývojového prostředí přečte soubor prostředků, která je vytvořena v jiné aplikaci, označí všechny zahrnuté záhlaví soubory jen pro čtení. Následně můžete použít [dialogové okno prostředek zahrnuje](../windows/resource-includes-dialog-box.md) přidat soubory hlaviček symbolů další jen pro čtení.  
  
 Jedním z důvodů, že které chcete použít jen pro čtení symbol definice je pro soubory symbolů, které chcete sdílet mezi několika projekty.  
  
 Můžete taky použít symbol zahrnuté soubory, pokud máte existující prostředky s symbol definice, které definují hodnotu symbol pomocí výrazy spíše než jednoduché celých čísel. Příklad:  
  
```  
#define   IDC_CONTROL1 2100  
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```  
  
 Prostředí bude správně interpretovat tyto počítané symboly stejně dlouho jako:  
  
-   Počítané symboly jsou umístěny v souboru symboly jen pro čtení.  
  
-   Váš soubor prostředků obsahuje prostředky, na které jsou již přiřazena tyto počítané symboly.  
  
-   Je očekáván číselný výraz.  
  
> [!NOTE]
>  Pokud je řetězec nebo číselný výraz očekávání, není tento výraz vyhodnocen.  
  
### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Chcete zahrnout do souboru prostředků sdílené symboly (jen pro čtení)  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na váš soubor .rc a zvolte [prostředek zahrnuje](../windows/resource-includes-dialog-box.md) z místní nabídky.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V **směrnice pro symboly jen pro čtení** pole, použijte **#include** kompilátoru direktiva Určuje soubor, kam má jen pro čtení symboly, které mají být zachovány.  
  
     Upravit soubor Resource.h, protože se název souboru normálně používat hlavičkový soubor hlavní symbol.  
  
    > [!NOTE]
    >  **Důležité** zadejte do pole jen pro čtení symbol direktivy je součástí souboru prostředků přesně tak, jak ji zadáte. Ujistěte se, co zadáte neobsahuje všechny chyby pravopis nebo syntaxe.  
  
     Použití **směrnice pro symboly jen pro čtení** políčko zahrnout soubory s definicemi symbol jenom. Nezahrnovat definice prostředků; definice duplicitní prostředků, jinak bude vytvořen, při uložení souboru.  
  
3.  Umístěte soubor, který jste zadali symboly.  
  
     Symboly v souborech, které jsou součástí tímto způsobem se vyhodnocují při každém otevření souboru prostředků, ale nejsou při ukládání souboru nahradit na disku.  
  
4.  Click **OK**.  
  

  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Omezení názvu symbolu](../windows/symbol-name-restrictions.md)   
 [Omezení hodnoty symbolu](../windows/symbol-value-restrictions.md)   
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)   
 [Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)