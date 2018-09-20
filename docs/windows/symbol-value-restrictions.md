---
title: Omezení hodnoty symbolu | Dokumentace Microsoftu
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
- symbols [C++], value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0f6939cfb9cd1dc72026441d946431097a5c3d7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375278"
---
# <a name="symbol-value-restrictions"></a>Omezení hodnoty symbolu

Symbol hodnota může být libovolné celé číslo vyjádřena v normálním způsobem pro # direktivy preprocesoru define. Tady jsou některé příklady hodnot symbolů:

```
18
4001
0x0012
-3456
```

Hodnoty symbolů pro prostředky (akcelerátory, rastrové obrázky, kurzory, dialogová okna, ikony, nabídky, tabulek řetězců a informace o verzi) musí být desítkové číslo v rozsahu od 0 do 32 767 (ale nemůže být šestnáctkové). Hodnoty symbolů pro části prostředků, jako jsou ovládací prvky dialogového okna nebo jednotlivé řetězce v tabulce řetězců může být od 0 do 65 534 nebo od-32 768 do 32 767.

Symboly prostředků jsou čísla 16 bitů. Můžete je zadat jako nebo bez znaménka, ale používá se interně jako celá čísla bez znaménka. Takže záporná čísla bude přetypovat na jejich odpovídající kladnou hodnotu.

Tady jsou některá omezení hodnoty symbolu:

- Vývojové prostředí sady Visual Studio a MFC používají některé počet rozsahů pro zvláštní účely. Všechna čísla sadou nejvýznamnější bit (-32 768 -1 a 32 768 do 65 534, v závislosti na znaménko) jsou vyhrazené knihovny MFC.

- Nejde definovat hodnotu symbolu pomocí jiných řetězců symbol. Například následující definice symbolu se nepodporuje:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Makra preprocesoru nelze použít s argumenty jako definice hodnot. Příklad:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   není platný výraz bez ohledu na to, co `ID` vyhodnocen v době kompilace.

- Vaše aplikace může mít existující soubor obsahující symboly definované s výrazy. Další informace o tom, jak zahrnout symboly jako jen pro čtení symbolů najdete v tématu [použití sdílených (jen pro čtení) nebo počítané symboly](../windows/including-shared-read-only-or-calculated-symbols.md).

Další informace o počet rozsahů, naleznete v tématu [TN023: standardní prostředky MFC](../mfc/tn023-standard-mfc-resources.md).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Změna číselné hodnoty symbolu](../windows/changing-a-symbol-s-numeric-value.md)<br/>
[Omezení názvu symbolu](../windows/symbol-name-restrictions.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)