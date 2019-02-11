---
title: Změna nebo odstranění nepřiřazených symbolů
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.unassigned
helpviewer_keywords:
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
ms.assetid: b6abee4a-3c24-4697-a166-fe6a86cad35f
ms.openlocfilehash: 47cc3d7a387092afe77fdbcf4bbdb6d085eeda25
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987011"
---
# <a name="changing-or-deleting-unassigned-symbols"></a>Změna nebo odstranění nepřiřazených symbolů

Během činnosti v [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md), můžete upravit nebo odstranit existující symboly, které nejsou přiřazeny k prostředku nebo objekt.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

## <a name="to-change-an-unassigned-symbol"></a>Změna nepřiřazených symbolů

1. V **název** vyberte nepřiřazených symbolů a vyberte **změnu**.

1. Upravit vlastnosti name nebo value v polí zobrazených v symbolu **změnit Symbol** dialogové okno.

   > [!NOTE]
   > Chcete-li změnit symbol, který *je* přiřazené k prostředku nebo k objektu, je nutné použít editor prostředků nebo **vlastnosti** okna. Další informace najdete v tématu [změna symbolu nebo názvu symbolu](../windows/changing-a-symbol-or-symbol-name-id.md).

## <a name="to-delete-an-unassigned-unused-symbol"></a>Chcete-li odstranit symbol nepřiřazené (nepoužívané)

V [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md), vyberte symbol, který chcete odstranit a zvolte **odstranit**.

   > [!NOTE]
   > Před odstraněním nepoužívaných symbolů do souboru prostředků, ujistěte se, že se nepoužívá jako jinde v programu ani soubory prostředků zahrnuté v době kompilace.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)<br/>
[Omezení názvu symbolu](../windows/symbol-name-restrictions.md)<br/>
[Omezení hodnoty symbolu](../windows/symbol-value-restrictions.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)