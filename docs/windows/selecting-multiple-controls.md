---
title: Výběr více ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- controls [C++], removing from groups
ms.assetid: efbdbade-0a3a-4328-b36e-a6376c06e8de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6789a378b163da9e3cefbabb506f84a3cb9a5d7f
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317774"
---
# <a name="selecting-multiple-controls"></a>Výběr více ovládacích prvků

### <a name="to-select-multiple-controls"></a>Výběr více ovládacích prvků

1. V [okno nástrojů](/visualstudio/ide/reference/toolbox), vyberte **ukazatel** nástroj.

2. Tažením nakreslete rámeček výběru okolo ovládací prvky, které chcete vybrat ve vašem dialogovém okně.

   Když uvolníte tlačítko myši, všechny řídí uvnitř a protínající se operátory jsou vybrané pole výběru.

   \- nebo –

- Podržte stisknutou klávesu **Shift** key a klikněte na ovládací prvky, které chcete zahrnout do výběru.

   \- nebo –

- Podržte stisknutou klávesu **Ctrl** key a klikněte na ovládací prvky, které chcete zahrnout do výběru.

### <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Odebrat ovládací prvek ze skupiny z vybraných ovládacích prvků nebo přidání ovládacího prvku na skupinu vybraných ovládacích prvků

1. Se skupinou vybraných ovládacích prvků, podržte stisknutou klávesu **Shift** key a klikněte na ovládací prvek, který chcete odstranit nebo přidat do existujícího výběru.

   > [!NOTE]
   > Podržení **Ctrl** klíč a klepnutí na ovládací prvek v rámci výběru způsobí, že, které řídí dominantního ovládacího prvku v tomto výběru. Další informace najdete v tématu [určení dominantního ovládacího prvku](../windows/specifying-the-dominant-control.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Výběr ovládacích prvků](../windows/selecting-controls.md)  
[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)