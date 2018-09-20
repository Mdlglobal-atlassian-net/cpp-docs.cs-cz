---
title: Úprava v tabulce akcelerátorů (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
ms.assetid: 545b650b-4f26-4b20-8431-d942548443bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 57347b88fe7d54813e06cde6d5f4b3414e79f116
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395803"
---
# <a name="editing-in-an-accelerator-table-c"></a>Úprava v tabulce akcelerátorů (C++)

### <a name="to-edit-in-an-accelerator-table"></a>Úprava v tabulce akcelerátorů

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Vyberte položku v tabulce a klikněte na tlačítko aktivovat místní úpravy.

3. Vyberte z rozevíracího seznamu nebo zadejte místo, kde můžete provádět změny.

   - Pro [ID](id-property.md), vyberte ze seznamu nebo typu, který chcete upravit.

   - Pro [modifikátor](../windows/accelerator-modifier-property.md), vyberte ze seznamu.

   - Pro [klíč](../windows/accelerator-key-property.md), vyberte ze seznamu nebo typu, který chcete upravit.

   - Pro [typ](../windows/accelerator-type-property.md)vyberte **ASCII** nebo **VIRTKEY** ze seznamu.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Úprava tabulek akcelerátorů](../windows/editing-accelerator-tables.md)<br/>
[Editor akcelerátorů](../windows/accelerator-editor.md)