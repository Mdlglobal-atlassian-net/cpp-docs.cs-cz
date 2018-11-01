---
title: Vytváření nových symbolů
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.creating
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 9305f5bf409d5c0d4da227d2aadd3f16dc85945c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600107"
---
# <a name="creating-new-symbols"></a>Vytváření nových symbolů

Když začínáte nový projekt, možná bude vhodné ke zmapování názvy symbolů, které budete potřebovat ještě před vytvořením prostředků, ke kterým bude přiřazena.

### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>Chcete-li vytvořit nový symbol pomocí dialogového okna symbolů prostředků

1. V [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md), zvolte **nový**.

2. V **název** zadejte název symbolu.

3. Přijměte hodnotu přiřazenou symbolu.

   -nebo-

   V **hodnotu** zadejte novou hodnotu.

4. Klikněte na tlačítko **OK** přidáte nový symbol do seznamu symbol.

Pokud zadáte název symbolu, který již existuje, zobrazí se okno se zprávou s informacemi o tom, že je již definován symbol s tímto názvem. Nejde definovat dvě nebo víc symbolů se stejným názvem, ale můžete definovat různé symbolů se stejnou číselnou hodnotu. Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md) a [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům zobrazení statických prostředků a přiřazování prostředků řetězců pro vlastnosti.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)