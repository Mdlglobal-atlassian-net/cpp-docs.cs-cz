---
title: Omezení hodnoty symbolu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.restrictions.value
dev_langs:
- C++
helpviewer_keywords:
- symbols, value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3432ca82d9557fbcb47da65be148bedb0f47f8b8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="symbol-value-restrictions"></a>Omezení hodnoty symbolu
Symbol hodnota může být libovolné celé vyjádřené běžným způsobem pro # direktivy preprocesoru define. Tady jsou některé příklady symbol hodnoty:  
  
```  
18  
4001  
0x0012  
-3456  
```  
  
 Hodnoty symbolů pro prostředky (akcelerátorů, rastrové obrázky, kurzory, dialogová okna, ikony, nabídek, tabulky řetězců a informace o verzi) musí být desítkové číslo v rozsahu od 0 do 32 767 (ale nesmí být šestnáctkové). Hodnoty symbolů pro části prostředky, například dialogové okno Ovládací prvky nebo jednotlivé řetězců v tabulce řetězec může být od 0 do 65,534 nebo od-32 768 do 32 767.  
  
 Symboly prostředků jsou čísla 16 bitů. Můžete je zadat jako podepsaný držitelem nebo bez znaménka, ale používají se interně jako celá čísla bez znaménka. Proto záporná čísla bude přetypovat na jejich odpovídající kladnou hodnotu.  
  
 Tady jsou některá omezení hodnoty symbolu:  
  
-   Vývojové prostředí sady Visual Studio a MFC používají některé počet rozsahů pro zvláštní účely. Všechna čísla s nastaveným bitem nejvýznamnějších (-1 nebo 32 768 k 65,534, v závislosti na přihlašovací-32 768) jsou vyhrazené MFC.  
  
-   Nelze definovat na hodnotu symbol pomocí jiných řetězců symbol. Například následující definice symbolu není podporována:  
  
    ```  
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported  
    ```  
  
-   Makra preprocesoru s argumenty nelze použít jako hodnotu definice. Příklad:  
  
    ```  
    #define   IDD_ABOUT  ID(7) //not supported  
    ```  
  
     není platný výraz bez ohledu na to, co `ID` vyhodnocen jako v době kompilace.  
  
-   Aplikace může mít existující soubor obsahující symboly definované s výrazy. Další informace o tom, jak obsahovat symboly jako symboly jen pro čtení najdete v tématu [pomocí sdílených (jen pro čtení) nebo vypočítat symboly](../windows/including-shared-read-only-or-calculated-symbols.md).  
  
 Další informace o počet rozsahů v tématu [TN023: standardní prostředky MFC](../mfc/tn023-standard-mfc-resources.md).  
  

  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Změna číselné hodnoty symbolu](../windows/changing-a-symbol-s-numeric-value.md)   
 [Omezení názvu symbolu](../windows/symbol-name-restrictions.md)   
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)