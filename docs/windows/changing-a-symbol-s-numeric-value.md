---
title: Změna symbolu&#39;s číselnou hodnotu
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.value
helpviewer_keywords:
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
ms.openlocfilehash: 9013ce886b1e596a858321b32249d885d03015ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629837"
---
# <a name="changing-a-symbol39s-numeric-value"></a>Změna symbolu&#39;s číselnou hodnotu

Pro symboly přidružený jeden prostředek, můžete použít [okno vlastností](/visualstudio/ide/reference/properties-window) Chcete-li změnit hodnotu symbolu. Můžete použít [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) ke změně hodnoty symbolů není aktuálně přiřazená k prostředku. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).

### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Chcete-li změnit hodnotu symbolu, která je přiřazena k jednomu prostředku nebo k objektu

1. V [zobrazení prostředků](../windows/resource-view-window.md), vyberte prostředek.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V **vlastnosti** okno, zadejte název symbolu následovaný symbolem rovná a typ integer v **ID** pole, například:

    ```
    IDC_EDITNAME=5100
    ```

Nová hodnota je uložena v hlavičkový soubor symbolů při příštím uložte projekt. Pouze název symbolu zůstává viditelná pole ID. rovnítko a hodnota se nezobrazují, až se ověří.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům zobrazení statických prostředků a přiřazování prostředků řetězců pro vlastnosti.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Omezení hodnoty symbolu](../windows/symbol-value-restrictions.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)